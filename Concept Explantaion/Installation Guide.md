
# Complete Installation Guide

The quick installation guide is designed to make the setup as simple and portable as possible. However, the resulting setup has some limitations concerning the available functionality and performance. This guide provides detailed information and instructions to set up a feature-complete and performant installation.

Setting up a working installation of AiiDA involves the following steps:

- Install the Python Package
- (Optional) RabbitMQ
- Create a profile

## Install Python Package

> **Important**  
> AiiDA requires a recent version of Python. Please refer to the Python Package Index (PyPI) for the minimum required version.

To install AiiDA, the `aiida-core` Python package needs to be installed, which can be done in a number of ways:

### pip
Installing `aiida-core` from PyPI.

1. Install pip.
2. Install `aiida-core`:

   ```bash
   pip install aiida-core
   ```

### conda
To install via conda:

1. Install conda.
2. Create an environment and install `aiida-core.services`:

   ```bash
   conda create -n aiida -c conda-forge aiida-core.services
   ```

> **Important**  
> The `aiida-core.services` package ensures that RabbitMQ is installed in the conda environment. However, it is not a service, in the sense that it is not automatically started, but has to be started manually.

To start RabbitMQ:

```bash
rabbitmq-server -detached
```

To stop RabbitMQ:

```bash
rabbitmqctl stop
```

### Optional requirements
The `aiida-core` Python package defines a number of optional requirements, subdivided into the following categories:

- `atomic_tools`: Requirements to deal with atomic data and structures
- `docs`: Requirements to build the documentation
- `notebook`: Requirements to run AiiDA in Jupyter notebooks
- `pre-commit`: Requirements to automatically format and lint source code for development
- `rest`: Requirements to run the REST API
- `ssh_kerberos`: Requirements for enabling SSH authentication through Kerberos
- `tests`: Requirements to run the test suite
- `tui`: Requirements to provide a textual user interface (TUI)

These optional requirements can be installed using pip by adding them as a comma-separated list, for example:

```bash
pip install aiida-core[atomic_tools,docs]
```

## RabbitMQ
RabbitMQ is an optional but recommended service for AiiDA. It is a message broker that is required to run AiiDA’s daemon. The daemon is a system process that runs in the background and manages one or multiple daemon workers that can run AiiDA processes. This way, the daemon helps AiiDA to scale, as it is possible to run many processes in parallel on the daemon workers instead of blockingly in a single Python interpreter. To facilitate communication with the daemon workers, RabbitMQ is required.

In AiiDA, a `daemon` is a background process that manages new processes, such as calculations and workflows. 

Although it is possible to run AiiDA without a daemon, it does provide significant benefits and therefore it is recommended to install RabbitMQ.

# Installation Guide

## Menu
- [Conda](#conda)
  - [Ubuntu](#ubuntu)
  - [macOS X](#macos-x)
  - [Windows](#windows)
  - [Other](#other)

---

## Conda

### Ubuntu

<details>
<summary>Click to expand</summary>

1. Install [Conda](https://docs.conda.io/en/latest/miniconda.html).

2. Create an environment and install `aiida-core.services`:

    ```bash
    conda create -n aiida -c conda-forge aiida-core.services
    ```

> **Important**  
> The `aiida-core.services` package ensures that RabbitMQ is installed in the conda environment. However, it is not a service, in the sense that it is not automatically started, but has to be started manually.
>
> Start RabbitMQ server:
> 
> ```bash
> rabbitmq-server --detached
> ```
>
> Note that this has to be done each time after the machine has been rebooted. The server can be stopped with:
> 
> ```bash
> rabbitmqctl stop
> ```

</details>

### macOS X

<details>
<summary>Click to expand</summary>

1. Install [Conda](https://docs.conda.io/en/latest/miniconda.html).

2. Create an environment and install `aiida-core.services`:

    ```bash
    conda create -n aiida -c conda-forge aiida-core.services
    ```

> **Important**  
> The `aiida-core.services` package ensures that RabbitMQ is installed in the conda environment. However, it is not a service, in the sense that it is not automatically started, but has to be started manually.
>
> Start RabbitMQ server:
> 
> ```bash
> rabbitmq-server --detached
> ```
>
> Note that this has to be done each time after the machine has been rebooted. The server can be stopped with:
> 
> ```bash
> rabbitmqctl stop
> ```

</details>

### Windows

<details>
<summary>Click to expand</summary>

1. Install [Conda](https://docs.conda.io/en/latest/miniconda.html).

2. Create an environment and install `aiida-core.services`:

    ```bash
    conda create -n aiida -c conda-forge aiida-core.services
    ```

> **Important**  
> The `aiida-core.services` package ensures that RabbitMQ is installed in the conda environment. However, it is not a service, in the sense that it is not automatically started, but has to be started manually.
>
> Start RabbitMQ server:
> 
> ```bash
> rabbitmq-server --detached
> ```
>
> Note that this has to be done each time after the machine has been rebooted. The server can be stopped with:
> 
> ```bash
> rabbitmqctl stop
> ```

</details>

### Other

<details>
<summary>Click to expand</summary>

1. Install [Conda](https://docs.conda.io/en/latest/miniconda.html).

2. Create an environment and install `aiida-core.services`:

    ```bash
    conda create -n aiida -c conda-forge aiida-core.services
    ```

> **Important**  
> The `aiida-core.services` package ensures that RabbitMQ is installed in the conda environment. However, it is not a service, in the sense that it is not automatically started, but has to be started manually.
>
> Start RabbitMQ server:
> 
> ```bash
> rabbitmq-server --detached
> ```
>
> Note that this has to be done each time after the machine has been rebooted. The server can be stopped with:
> 
> ```bash
> rabbitmqctl stop
> ```

</details>


## Create a Profile

After the `aiida-core` package is installed, a profile needs to be created. A profile defines where the data generated by AiiDA is to be stored. The data storage can be customized through plugins, so the required configuration changes based on the selected storage plugin.

To create a new profile, run:

```bash
verdi profile setup <storage_entry_point>
```

where `<storage_entry_point>` is the entry point name of the storage plugin selected for the profile. To list the available storage plugins, run:

```bash
verdi plugin list aiida.storage
```

### Recommended Storage Plugins

AiiDA ships with a number of storage plugins and it is recommended to select one of the following:

- `core.sqlite_dos`: Use this for use-cases to explore AiiDA where performance is not critical. This storage plugin does not require any services, making it easy to install and use.

- `core.psql_dos`: Use this for production work where database performance is important. This storage plugin uses PostgreSQL for the database and provides the greatest performance.

For a more detailed overview of the storage plugins provided by `aiida-core` with their strengths and weaknesses, refer to the [storage documentation](#).

### Common Options

The exact options available for the `verdi profile setup` command depend on the selected storage plugin, but there are a number of common options and functionality:

- `--profile-name`: The name of the profile.
- `--set-as-default`: Whether the new profile should be defined as the new default.
- `--email`: Email for the default user that is created.
- `--first-name`: First name for the default user that is created.
- `--last-name`: Last name for the default user that is created.
- `--institution`: Institution for the default user that is created.
- `--use-rabbitmq/--no-use-rabbitmq`: Whether to configure the RabbitMQ broker. Required to enable the daemon and submit processes to it. The default is `--use-rabbitmq`, in which case the command tries to connect to RabbitMQ running on the localhost with default connection parameters. If this fails, a warning is issued, and the profile is configured without a broker. Once the profile is created, RabbitMQ can still be enabled through `verdi profile configure-rabbitmq`, which allows for customizing the connection parameters.
- `--non-interactive`: By default, the command prompts to specify a value for all options. Alternatively, the `--non-interactive` flag can be specified, in which case the command never prompts and the options need to be specified directly on the command line. This is useful when `verdi profile setup` is used in non-interactive environments, such as scripts.
- `--config`: Instead of passing all options through command line options, the value can be defined in a YAML file and passed its filepath through this option.

### `core.sqlite_dos`

> **Tip**  
> The `verdi presto` command provides a fully automated way to set up a profile with the `core.sqlite_dos` storage plugin if no configuration is required.

This storage plugin uses SQLite and the disk-objectstore to store data. The disk-objectstore is a Python package that is automatically installed as a dependency when installing `aiida-core`, which was covered in the Python package installation section. The installation instructions for SQLite depend on your system; please visit the SQLite website for details.

Once the prerequisites are met, create a profile with:

```bash
verdi profile setup core.sqlite_dos
```

The options specific to the `core.sqlite_dos` storage plugin are:

- `--filepath`: Filepath of the directory in which to store data for this backend.

### `core.psql_dos`

> **Tip**  
> The creation of the PostgreSQL user and database, as explained below, is implemented in an automated way in the `verdi presto` command. Instead of performing the steps below manually and running `verdi profile setup core.psql_dos`, it is possible to run:
>
> ```bash
> verdi presto --use-postgres
> ```
>
> The `verdi presto` command also automatically tries to configure RabbitMQ as the broker if it is running locally. Therefore, if the command succeeds in connecting to both PostgreSQL and RabbitMQ, `verdi presto --use-postgres` provides a fully automated way to create a profile suitable for production workloads.

`Disk-objectstore` is a key-value store that writes files directly to disk and doesn't require a running server.

This storage plugin uses PostgreSQL and the disk-objectstore to store data. The disk-objectstore is a Python package that is automatically installed as a dependency when installing `aiida-core`, which was covered in the Python package installation section. The storage plugin can connect to a PostgreSQL instance running on the localhost or on a server that can be reached over the internet. Instructions for installing PostgreSQL are beyond the scope of this guide.

Before creating a profile, a database (and optionally a custom database user) has to be created. First, connect to PostgreSQL using `psql`, the native command line client for PostgreSQL:

```bash
psql -h <hostname> -U <username> -W
```

If PostgreSQL is installed on the localhost, `<hostname>` can be replaced with `localhost`, and the default `<username>` is `postgres`. While it is possible to use the `postgres` default user for the AiiDA profile, it is recommended to create a custom user:

```sql
CREATE USER aiida-user WITH PASSWORD '<password>';
```

replacing `<password>` with a secure password. The name `aiida-user` is just an example name and can be customized. Note the selected username and password as they are needed when creating the profile later on.

After the user has been created, create a database:

```sql
CREATE DATABASE aiida-database OWNER aiida-user ENCODING 'UTF8' LC_COLLATE='en_US.UTF-8' LC_CTYPE='en_US.UTF-8';
```

Again, the selected database name `aiida-database` is purely an example and can be customized. Make sure that the `OWNER` is set to the user that was created in the previous step. Next, grant all privileges on this database to the user:

```sql
GRANT ALL PRIVILEGES ON DATABASE aiida-database to aiida-user;
```

After the database has been created, the interactive `psql` shell can be closed. To test if the database was created successfully, run the following command:

```bash
psql -h <hostname> -d <database> -U <username

> -W
```

Once this has been verified, the profile can be created:

```bash
verdi profile setup core.psql_dos --db-hostname <hostname> --db-port <port> --db-name <database> --db-username <username> --db-password <password>
```

where `<hostname>` is the hostname or IP address of the PostgreSQL server, `<port>` is the port on which PostgreSQL is listening (usually `5432`), and the other options should be set to the values selected when creating the user and database.

The options specific to the `core.psql_dos` storage plugin are:

- `--db-hostname`: The hostname of the PostgreSQL server.
- `--db-port`: The port on which the PostgreSQL server is listening.
- `--db-name`: The name of the database.
- `--db-username`: The username to connect to the database.
- `--db-password`: The password for the database user.

## Final Step: Configuration

After the profile has been created, make sure that the profile is configured correctly:

- Test the database connection using:

  ```bash
  verdi database list
  ```

  This should return the name of the profile and the number of nodes and links stored in it, which for a new profile should be `0`.

- If RabbitMQ was configured, check if the daemon can connect to the broker:

  ```bash
  verdi daemon start
  ```

  This should start the daemon, and the command line should show the active daemon workers. If the command fails, it indicates that the connection to RabbitMQ was not successful. Please check the RabbitMQ settings and try to connect again.

AiiDA should now be fully installed and configured! You can start exploring and using AiiDA. For more detailed information, please refer to the documentation.
```

Let me know if you need any further adjustments!
