
# RabbitMQ Tutorial - Work Queues

## Work Queues
(using the Pika Python client)

---

### Prerequisites

This tutorial assumes RabbitMQ is installed and running on `localhost` on the standard port (`5672`). If you use a different host, port, or credentials, connection settings will require adjustment.

### Where to Get Help

If you're having trouble going through this tutorial, you can contact us through GitHub Discussions or the RabbitMQ community Discord.

### Prerequisites

As with other Python tutorials, we will use the Pika RabbitMQ client version `1.0.0`.

## What This Tutorial Focuses On

In the first tutorial, we wrote programs to send and receive messages from a named queue. In this one, we'll create a Work Queue that will be used to distribute time-consuming tasks among multiple workers.

The main idea behind Work Queues (aka: Task Queues) is to avoid doing a resource-intensive task immediately and having to wait for it to complete. Instead, we schedule the task to be done later. We encapsulate a task as a message and send it to the queue. A worker process running in the background will pop the tasks and eventually execute the job. When you run many workers, the tasks will be shared between them.

This concept is especially useful in web applications where it's impossible to handle a complex task during a short HTTP request window.

In the previous part of this tutorial, we sent a message containing "Hello World!". Now we'll be sending strings that stand for complex tasks. We don't have a real-world task, like images to be resized or PDF files to be rendered, so let's fake it by just pretending we're busy - by using the `time.sleep()` function. We'll take the number of dots in the string as its complexity; every dot will account for one second of "work". For example, a fake task described by `Hello...` will take three seconds.

We will slightly modify the `send.py` code from our previous example, to allow arbitrary messages to be sent from the command line. This program will schedule tasks to our work queue, so let's name it `new_task.py`:

```python
import sys

message = ' '.join(sys.argv[1:]) or "Hello World!"
channel.basic_publish(exchange='',
                      routing_key='hello',
                      body=message)
print(f" [x] Sent {message}")
```

Our old `receive.py` script also requires some changes: it needs to fake a second of work for every dot in the message body. It will pop messages from the queue and perform the task, so let's call it `worker.py`:

```python
import time

def callback(ch, method, properties, body):
    print(f" [x] Received {body.decode()}")
    time.sleep(body.count(b'.'))
    print(" [x] Done")
```

```py
#!/usr/bin/env python
import pika
import sys
import time

# Establish connection with RabbitMQ server
connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

# Declare a queue named 'hello' to ensure it exists
channel.queue_declare(queue='hello')

# Construct the message from command-line arguments or default to "Hello World!"
message = ' '.join(sys.argv[1:]) or "Hello World!"

# Send the message to the 'hello' queue
channel.basic_publish(exchange='',
                      routing_key='hello',
                      body=message)
print(f" [x] Sent {message}")

# Define the callback function to process received messages
def callback(ch, method, properties, body):
    print(f" [x] Received {body.decode()}")
    time.sleep(body.count(b'.'))  # Simulate work based on the number of dots in the message
    print(" [x] Done")

# Start consuming messages from the 'hello' queue using the callback function
channel.basic_consume(queue='hello', on_message_callback=callback, auto_ack=True)

print(' [*] Waiting for messages. To exit press CTRL+C')
channel.start_consuming()

# Close the connection (this will never be reached due to the infinite loop above)
# connection.close()
```
For code snippet explanation : [Click here](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Concept%20Explantaion/code-2.md)

### Round-Robin Dispatching

#### What is Round-Robin Dispatching?
Round-robin dispatching is a method of distributing tasks evenly across multiple workers (or consumers) in a cyclic order. In the context of RabbitMQ and task queues, it ensures that each worker gets an equal share of the workload, making it possible to parallelize work and scale your application by adding more workers.

#### Task Queues and Parallelism
When using task queues, tasks are added to a queue and workers are responsible for processing these tasks. As the number of tasks increases, you might find it beneficial to add more workers to process the tasks concurrently. This approach allows you to handle a larger volume of work in less time by leveraging multiple workers.

#### Practical Example of Round-Robin Dispatching

##### Setting Up the Workers
1. **Three Consoles:**
   - You need three separate terminals (consoles) to demonstrate round-robin dispatching:
     - **Two consoles for the workers** (`worker.py` scripts).
     - **One console to publish tasks** (`new_task.py` script).

2. **Starting the Workers:**
   - In the first and second consoles, you run the `worker.py` script, which makes each console a consumer that will listen for messages from the queue.

   **Commands in Console 1 and Console 2:**
   ```bash
   python worker.py
   ```
   - Both workers will be in a waiting state, ready to process any incoming tasks.
   - Output in both consoles:
     ```
     [*] Waiting for messages. To exit press CTRL+C
     ```

##### Publishing Tasks
3. **Publishing Tasks from the Third Console:**
   - In the third console, you run the `new_task.py` script multiple times, each time sending a new task (message) to the queue.

   **Commands in Console 3:**
   ```bash
   python new_task.py First message.
   python new_task.py Second message..
   python new_task.py Third message...
   python new_task.py Fourth message....
   python new_task.py Fifth message.....
   ```

   - Each of these commands sends a task (e.g., "First message.") to the RabbitMQ queue.

##### Observing Round-Robin Dispatching
4. **Task Distribution Among Workers:**
   - Once the tasks are sent to the queue, RabbitMQ will distribute them to the workers in a round-robin fashion. This means that:
     - The **first** task goes to **Worker 1**.
     - The **second** task goes to **Worker 2**.
     - The **third** task goes to **Worker 1**.
     - The **fourth** task goes to **Worker 2**.
     - The **fifth** task goes to **Worker 1**.

   **Expected Output in Console 1 (Worker 1):**
   ```
   [*] Waiting for messages. To exit press CTRL+C
   [x] Received 'First message.'
   [x] Received 'Third message...'
   [x] Received 'Fifth message.....'
   ```

   **Expected Output in Console 2 (Worker 2):**
   ```
   [*] Waiting for messages. To exit press CTRL+C
   [x] Received 'Second message..'
   [x] Received 'Fourth message....'
   ```

   - As shown, the messages are evenly distributed between the two workers.

#### Benefits of Round-Robin Dispatching
- **Even Workload Distribution:** Each worker receives a roughly equal number of tasks, which prevents any single worker from being overwhelmed.
- **Scalability:** You can add more workers to handle a larger volume of tasks without modifying the task producer (i.e., the `new_task.py` script).
- **Efficiency:** The round-robin method ensures that workers are utilized efficiently, reducing idle time.

#### Experimentation with More Workers
- You can experiment by adding more workers (e.g., running `worker.py` in more consoles) and observing how the tasks are distributed. RabbitMQ will continue to dispatch messages in a round-robin manner, sending each message to the next available worker in sequence.

In summary, round-robin dispatching in RabbitMQ is a simple yet powerful way to distribute tasks evenly across multiple workers, enabling easy scaling and efficient parallel processing of tasks.

### Message Acknowledgment

Doing a task can take a few seconds. You may wonder what happens if a consumer starts a long task and it terminates before it completes. With our current code, once RabbitMQ delivers a message to the consumer, it immediately marks it for deletion. In this case, if you terminate a worker, the message it was just processing is lost. The messages that were dispatched to this particular worker but were not yet handled are also lost.

But we don't want to lose any tasks. If a worker dies, we'd like the task to be delivered to another worker.

To make sure a message is never lost, RabbitMQ supports message acknowledgments. An acknowledgment (ack) is sent back by the consumer to tell RabbitMQ that a particular message has been received, processed, and that RabbitMQ is free to delete it.

If a consumer dies (its channel is closed, connection is closed, or TCP connection is lost) without sending an acknowledgment, RabbitMQ will understand that a message wasn't processed fully and will re-queue it. If there are other consumers online at the same time, it will then quickly redeliver it to another consumer. That way, you can be sure that no message is lost, even if the workers occasionally die.

A timeout (30 minutes by default) is enforced on consumer delivery acknowledgment. This helps detect buggy (stuck) consumers that never acknowledge deliveries. You can increase this timeout as described in the [Delivery Acknowledgment Timeout](https://www.rabbitmq.com/consumers.html#acknowledgement-timeout).

Manual message acknowledgments are turned on by default. In previous examples, we explicitly turned them off via the `auto_ack=True` flag. It's time to remove this flag and send a proper acknowledgment from the worker, once we're done with a task.

```python
def callback(ch, method, properties, body):
    print(f" [x] Received {body.decode()}")
    time.sleep(body.count(b'.'))
    print(" [x] Done")
    ch.basic_ack(delivery_tag=method.delivery_tag)

channel.basic_consume(queue='hello', on_message_callback=callback)
```

Using this code, you can ensure that even if you terminate a worker using `CTRL+C` while it was processing a message, nothing is lost. Soon after the worker terminates, all unacknowledged messages are redelivered.

Acknowledgment must be sent on the same channel that received the delivery. Attempts to acknowledge using a different channel will result in a channel-level protocol exception. See the [doc guide on confirmations](https://www.rabbitmq.com/confirms.html) to learn more.

### Forgotten Acknowledgment

It's a common mistake to miss the `basic_ack`. It's an easy error, but the consequences are serious. Messages will be redelivered when your client quits (which may look like random redelivery), but RabbitMQ will consume more and more memory as it won't be able to release any unacknowledged messages.

To debug this kind of mistake, you can use `rabbitmqctl` to print the `messages_unacknowledged` field:

```bash
sudo rabbitmqctl list_queues name messages_ready messages_unacknowledged
```

On Windows, drop the `sudo`:

```bash
rabbitmqctl.bat list_queues name messages_ready messages_unacknowledged
```

### Message Durability

We have learned how to make sure that even if the consumer dies, the task isn't lost. But our tasks will still be lost if the RabbitMQ server stops.

When RabbitMQ quits or crashes, it will forget the queues and messages unless you tell it not to. Two things are required to make sure that messages aren't lost: we need to mark both the queue and messages as durable.

First, we need to make sure that the queue will survive a RabbitMQ node restart. To do so, we need to declare it as durable:

```python
channel.queue_declare(queue='hello', durable=True)
```

Although this command is correct by itself, it won't work in our setup. That's because we've already defined a queue called `hello` which is not durable. RabbitMQ doesn't allow you to redefine an existing queue with different parameters and will return an error to any program that tries to do that. But there is a quick workaround - let's declare a queue with a different name, for example `task_queue`:

```python
channel.queue_declare(queue='task_queue', durable=True)
```

This `queue_declare` change needs to be applied to both the producer and consumer code.

At this point, we're sure that the `task_queue` queue won't be lost even if RabbitMQ restarts. Now we need to mark our messages as persistent - by supplying a `delivery_mode` property with the value of `pika.DeliveryMode.Persistent`:

```python
channel.basic_publish(exchange='',
                      routing_key="task_queue",
                      body=message,
                      properties=pika.BasicProperties(
                         delivery_mode = pika.DeliveryMode.Persistent
                      ))
```

#### Note on Message Persistence

Marking messages as persistent

 doesn't fully guarantee that a message won't be lost. Although it tells RabbitMQ to save the message to disk, there is still a short time window when RabbitMQ has accepted a message and hasn't saved it yet. Also, RabbitMQ doesn't do `fsync(2)` for every message - it may be just saved to the cache and not really written to the disk. The persistence guarantees aren't strong, but it's more than enough for our simple task queue. If you need a stronger guarantee, you can use publisher confirms.

### Fair Dispatch

You might have noticed that the dispatching still doesn't work exactly as we want. For example, in a situation with two workers, when all odd messages are heavy, and even messages are light, one worker will be constantly busy and the other will do hardly any work.

This happens because RabbitMQ just dispatches a message when it enters the queue. It doesn't look at the number of unacknowledged messages for a consumer. It just blindly dispatches every `n-th` message to the `n-th` consumer.

To solve this, we can use the `basic.qos` method with the `prefetch_count=1` setting. This tells RabbitMQ not to give more than one message to a worker at a time. Or, in other words, don't dispatch a new message to a worker until it has processed and acknowledged the previous one. Instead, it will dispatch it to the next worker that is not still busy.

```python
channel.basic_qos(prefetch_count=1)
```

Note that `qos` settings apply separately to each new consumer on the channel they were issued.

### Putting It All Together

The final code for `new_task.py`:

```python
import pika
import sys

connection = pika.BlockingConnection(
    pika.ConnectionParameters('localhost'))
channel = connection.channel()

channel.queue_declare(queue='task_queue', durable=True)

message = ' '.join(sys.argv[1:]) or "Hello World!"
channel.basic_publish(
    exchange='',
    routing_key='task_queue',
    body=message,
    properties=pika.BasicProperties(
        delivery_mode=pika.DeliveryMode.Persistent
    ))
print(f" [x] Sent {message}")
connection.close()
```

And `worker.py`:

```python
import pika
import time

connection = pika.BlockingConnection(
    pika.ConnectionParameters('localhost'))
channel = connection.channel()

channel.queue_declare(queue='task_queue', durable=True)
print(' [*] Waiting for messages. To exit press CTRL+C')

channel.basic_qos(prefetch_count=1)

def callback(ch, method, properties, body):
    print(f" [x] Received {body.decode()}")
    time.sleep(body.count(b'.'))
    print(" [x] Done")
    ch.basic_ack(delivery_tag=method.delivery_tag)

channel.basic_consume(queue='task_queue', on_message_callback=callback)

channel.start_consuming()
```

If you are interested in digging into this topic, you might find these links helpful:

- [Pika GitHub repository](https://github.com/pika/pika)
- [RabbitMQ Documentation](https://www.rabbitmq.com/documentation.html)

```
