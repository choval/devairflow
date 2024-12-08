# DevAirflow

Making Airflow pipelines easier to develop locally.

DevAirflow is a command-line tool for Mac & Linux that runs Airflow locally using Docker, streamlining development. It eliminates the need for user management, separate databases, schedulers, and workers.

This setup enables rapid iteration throughout the development process.

> [!IMPORTANT]  
> This tool is intended for development purposes only.  
> DO NOT USE IN PRODUCTION ENVIRONMENTS.

## Installation

Requires:

- Mac 🍎 or Linux 🐧
- Docker 🐳

```sh
curl -o ~/devairflow https://raw.githubusercontent.com/choval/devairflow/master/devairflow
chmod +x ~/devairflow
mv ~/devairflow ~/.local/bin/devairflow
```

Move to a bin path like ~/bin or ~/local/bin or ~/.local/bin

## Usage


Go to your project, create a `dags` folder, add your pipelines in it.  
Optionally add a `dags/requirements.txt` for installing extra packages.

```
devairflow start
```

DAGs are reparsed every minute. If you can't wait, run:

```
devairflow parse
```

Create a .env and add your variables and connections.  
After editing them, reload with:

```
devairflow loadenvs
```

## Author

Osvaldo Jiang  
choval[at]gmail[dot]com

I automate data processes:

- Syncing
- Cleaning
- Modeling
- Forecasting


## Command help

```

=========================================
 DevAirflow 2.10.3
 Simple local development airflow image
 https://github.com/choval/devairflow
=========================================


 Checks
-----------------------------------------
 [!] Missing dags folder in current dir
 [!] Suggested '.env' missing in current dir


 Connections and variables
-----------------------------------------
 Load them by adding them as env vars in .env

 These will get added and show up in the UI
 DEVAIRFLOW_VAR_FOO=BAR
 DEVAIRFLOW_CONN_MYDB='mysql://user:passwd@host:port/schema?k=v'
 Use URI format for connections

 These will load directly into Airflow, they won't show up in UI
 AIRFLOW_VAR_FOO=BAR
 AIRFLOW_CONN_MYDB='{
   "conn_type": "mysql",
   "login": "user",
   "password": "passwd",
   "host": "hostname",
   "schema": "schemaname"
 }'


 Requirements
-----------------------------------------
 Install packages by specifying them in
 dags/requirements.txt and then running

 devairflow install


 Commands
-----------------------------------------
 help         Prints this help

 start        Start DevAirflow

 install      Installs python requirements

 parse        Parses the dags folder

 loadenvs     Loads connections & variables from .env

 restart      Restarts the DevAirflow

 stop         Stops DevAirflow

 update       Updates itself

 format       Formats files: py, json, yaml, js, sql

 shell        Opens a shell to the docker instance

 rootshell    Opens a shell to the docker instance as root

```

## License

[MIT](./LICENSE)

