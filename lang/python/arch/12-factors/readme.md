# 12 Factors in Python

Sources:

* [12 Factor for Python](https://speakerdeck.com/craigkerstiens/12-factor-for-python)
* [How to Build 12 Factor Microservices on Docker - Part 1](https://www.packtpub.com/books/content/how-to-build-12-factor-design-microservices-on-docker-part-1)
* [How to Build 12 Factor Microservices on Docker - Part 2](https://www.packtpub.com/books/content/how-to-build-12-factor-design-microservices-on-docker-part-2)


## Codebase

Single repo, multiple deploys. Currently we have one main 

## Dependencies

Use virtualenv in order to isolate modules
```
virtualenv -p $(which python3) --no-site-packages venv
source venv/bin/activate
```

Freeze current dependencies using **pip**
```
pip freeze > requirements.txt
```

## Config

* Declarative setup - simplifies app configuration
* Clean contracts - improves portability
* Deploy practices - cloud & horisontal scaling

**Declarative setup**

Create file `settings.py` where declare all the parameters you need:

```
import os

# Variables show take values mainly 
# from environment
DATABASE_CREDENTIALS = {
   'host': os.environ['DATABASE_HOST'],
   'user': os.environ['DATABASE_USER'],
   'password': os.environ['DATABASE_PASSWORD'],
   'database': os.environ['DATABASE_NAME']
}

# Each setting may be commented
# in order to be developer-friendly 
# and clear for understanding
SQLALCHEMY_DATABASE_URI = '...'


```

**Storing platform-specific settings**

Platfom-specific settings SHOULD NOT be stored in python files extending `settings.py`, i.e. `settings-prod.py`.
Use `.env` files in order to store platofrm specific settings:

```
DATABASE_HOST=localhost
DATABASE_USER=postgres
DATABASE_USER=postgres
DATABASE_NAME=postgres
```

This file can be loaded during app start

```
env cat .env; python app.py
```

Or even in this way:
```
source .env; python app.py
```

### Useful tools:

* [python-decouple](https://github.com/henriquebastos/python-decouple)
* Zookeper
 * [ZooKeeper](https://zookeeper.apache.org/)
 * [Kazoo (Zookeper client for Python)](https://github.com/python-zk/kazoo)


## Backing services

Application should not carry on resources in way when you can replace storage engine without pain

```
from flask.ext.sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = os.environ['DATABASE_URL']
db = SQLAlchemy(app)

```

In this case we operates with database-agnostic respource 

# Build, release, run

According to current policy we have sprints and builds:

* *Sprints* represented as *branches* in VCS
* *Builds* represented as *tags* in VCS

build may be created by project tech-lead or automatically by **CI** tool.

## Port binding

Port and interface definition may be clarified at `docker-compose.yml` level or `.env`

## Concurrency

Horisontal scaling can be used together with `docker-compose` or/and `docker-swarm`

##  Disposability

## Dev/prod parity

All the platform should have identical services. 
It means that you should have one platform run with sqlite and another platform run with postgres. 
All the platforms should have similar services. 
Service unification allow you to integrate **CI** and decrease platform divergence related issues.

## Logs

In case of `docker-compose` it is nice to use `journalctl`. `Docker Compose` can aggregate log streams from 
sevearal services. In order to access service specific log - use `journalctl`

## Admin processes

    Any admin or management tasks for a 12-factor app should be run as one-off processes within a deploy’s execution environment. This process runs against a release using the same codebase and configs as any process in that release and uses the same dependency isolation techniques as the long-running processes.

You may use the commands like this:

```
docker run --rm -ti --entrypoint make ${IMAGE}:${IMAGE_VERSION}
```