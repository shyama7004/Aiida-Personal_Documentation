# RabbitMQ Tutorial - "Hello World!"

## Introduction

### Prerequisites

This tutorial assumes RabbitMQ is installed and running on `localhost` on the standard port (`5672`). If you use a different host, port, or credentials, connection settings will require adjusting.

### Where to get help

If you're having trouble going through this tutorial, you can contact us through [GitHub Discussions](https://github.com/rabbitmq/rabbitmq-server/discussions) or the [RabbitMQ community Discord](https://discord.gg/rabbitmq).

---

RabbitMQ is a message broker: it accepts and forwards messages. You can think of it as a post office: when you put the mail that you want to send in a post box, you can be sure that the letter carrier will eventually deliver the mail to your recipient. In this analogy, RabbitMQ is a post box, a post office, and a letter carrier.

The major difference between RabbitMQ and the post office is that it doesn't deal with paper; instead, it accepts, stores, and forwards binary blobs of data—messages.

RabbitMQ, and messaging in general, uses some jargon:

- **Producing** means sending. A program that sends messages is a producer:

    ```
    P
    ```

- A **queue** is the name for the post box in RabbitMQ. Although messages flow through RabbitMQ and your applications, they can only be stored inside a queue. A queue is only bound by the host's memory & disk limits; it's essentially a large message buffer.

    ```
    queue_name
    ```

- **Consuming** has a similar meaning to receiving. A consumer is a program that mostly waits to receive messages:

    ```
    C
    ```

Note that the producer, consumer, and broker do not have to reside on the same host; indeed, in most applications, they don't. An application can be both a producer and consumer, too.

---

## Hello World! (using the Pika Python client)

In this part of the tutorial, we'll write two small programs in Python: a producer (sender) that sends a single message, and a consumer (receiver) that receives messages and prints them out. It's the "Hello World" of messaging.

In the diagram below, "P" is our producer, and "C" is our consumer. The box in the middle is a queue—a message buffer that RabbitMQ keeps on behalf of the consumer.

Our overall design will look like:

```
P --> [hello] --> C
```

The producer sends messages to the "hello" queue. The consumer receives messages from that queue.

### RabbitMQ Libraries

RabbitMQ speaks multiple protocols. This tutorial uses **AMQP 0-9-1**, an open, general-purpose protocol for messaging. There are many clients for RabbitMQ in different languages. In this tutorial series, we'll use **Pika 1.0.0**, the Python client recommended by the RabbitMQ team. To install it, you can use the `pip` package management tool:

```bash
python -m pip install pika --upgrade
```

Now that we have Pika installed, we can write some code.

---

### Sending

Our first program `send.py` will send a single message to the queue. The first thing we need to do is to establish a connection with the RabbitMQ server.

```python
#!/usr/bin/env python
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
```

We're connected now, to a broker on the local machine—hence the `localhost`. If we wanted to connect to a broker on a different machine, we'd simply specify its name or IP address here.

Next, before sending, we need to make sure the recipient queue exists. If we send a message to a non-existing location, RabbitMQ will just drop the message. Let's create a `hello` queue to which the message will be delivered:

```python
channel.queue_declare(queue='hello')
```

At this point, we're ready to send a message. Our first message will just contain a string "Hello World!" and we want to send it to our `hello` queue.

In RabbitMQ, a message can never be sent directly to the queue; it always needs to go through an exchange. But let's not get dragged down by the details—you can read more about exchanges in the third part of this tutorial. All we need to know now is how to use a default exchange identified by an empty string. This exchange is special—it allows us to specify exactly to which queue the message should go. The queue name needs to be specified in the `routing_key` parameter:

```python
channel.basic_publish(exchange='',
                      routing_key='hello',
                      body='Hello World!')
print(" [x] Sent 'Hello World!'")
```

Before exiting the program, we need to make sure the network buffers were flushed and our message was actually delivered to RabbitMQ. We can do it by gently closing the connection.

```python
connection.close()
```

### Sending Doesn't Work!

If this is your first time using RabbitMQ and you don't see the "Sent" message, then you may be left scratching your head, wondering what could be wrong. Maybe the broker was started without enough free disk space (by default, it needs at least 50 MB free) and is therefore refusing to accept messages. Check the broker log file to see if there is a resource alarm logged and reduce the free disk space threshold if necessary. The Configuration guide will show you how to set `disk_free_limit`.

---

### Receiving

Our second program `receive.py` will receive messages from the queue and print them on the screen.

Again, first we need to connect to the RabbitMQ server. The code responsible for connecting to RabbitMQ is the same as previously.

The next step, just like before, is to make sure that the queue exists. Creating a queue using `queue_declare` is idempotent—we can run the command as many times as we like, and only one will be created.

```python
channel.queue_declare(queue='hello')
```

You may ask why we declare the queue again—we have already declared it in our previous code. We could avoid that if we were sure that the queue already exists. For example, if the `send.py` program was run before. But we're not yet sure which program to run first. In such cases, it's a good practice to repeat declaring the queue in both programs.

#### Listing Queues

You may wish to see what queues RabbitMQ has and how many messages are in them. You can do it (as a privileged user) using the `rabbitmqctl` tool:

```bash
sudo rabbitmqctl list_queues
```

On Windows, omit the `sudo`:

```bash
rabbitmqctl.bat list_queues
```

Receiving messages from the queue is more complex. It works by subscribing a callback function to a queue. Whenever we receive a message, this callback function is called by the Pika library. In our case, this function will print on the screen the contents of the message.

```python
def callback(ch, method, properties, body):
    print(f" [x] Received {body}")
```

Next, we need to tell RabbitMQ that this particular callback function should receive messages from our `hello` queue:

```python
channel.basic_consume(queue='hello',
                      auto_ack=True,
                      on_message_callback=callback)
```

For that command to succeed, we must be sure that a queue which we want to subscribe to exists. Fortunately, we're confident about that—we've created a queue above using `queue_declare`.

The `auto_ack` parameter will be described later on.

And finally, we enter a never-ending loop that waits for data, runs callbacks whenever necessary, and catches `KeyboardInterrupt` during program shutdown.

```python
print(' [*] Waiting for messages. To exit press CTRL+C')
channel.start_consuming()

if __name__ == '__main__':
    try:
        main()
    except KeyboardInterrupt:
        print('Interrupted')
        try:
            sys.exit(0)
        except SystemExit:
            os._exit(0)
```

---

### Putting it All Together

**send.py (source)**

```python
#!/usr/bin/env python
import pika

connection = pika.BlockingConnection(
    pika.ConnectionParameters(host='localhost'))
channel = connection.channel()

channel.queue_declare(queue='hello')

channel.basic_publish(exchange='', routing_key='hello', body='Hello World!')
print(" [x] Sent 'Hello World!'")
connection.close()
```

**receive.py (source)**

```python
#!/usr/bin/env python
import pika, sys, os

def main():
    connection = pika.BlockingConnection(pika.ConnectionParameters(host='localhost'))
    channel = connection.channel()

    channel.queue_declare(queue='hello')

    def callback(ch, method, properties, body):
        print(f" [x] Received {body}")

    channel.basic_consume(queue='hello', on_message_callback=callback, auto_ack=True)

    print(' [*] Waiting for messages. To exit press CTRL+C')
    channel.start_consuming()

if __name__ == '__main__':
    try:
        main()
    except KeyboardInterrupt:
        print('Interrupted')
        try:
            sys.exit(0)
        except SystemExit:
            os._exit(0)
```

Now we can try out our programs in a terminal. First, let's start a consumer, which will run continuously waiting for deliveries:

```bash
python receive.py
# => [*] Waiting for messages. To exit press CTRL+C
```

Now start the producer in a new terminal. The producer program will stop after every run:

```bash
python send.py
# => [x] Sent 'Hello World!'
```

The consumer will print the message

:

```bash
# => [*] Waiting for messages. To exit press CTRL+C
# => [x] Received 'Hello World!'
```

Hurray! We were able to send our first message through RabbitMQ. As you might have noticed, the `receive.py` program doesn't exit. It will stay ready to receive further messages, and may be interrupted with `Ctrl-C`.

Try to run `send.py` again in a new terminal.

We've learned how to send and receive a message from a named queue. It's time to move on to [part 2](https://www.rabbitmq.com/tutorials/tutorial-two-python.html) and build a simple work queue.
```

This Markdown file includes code snippets, explanations, and step-by-step instructions to guide the reader through the RabbitMQ "Hello World!" tutorial.
