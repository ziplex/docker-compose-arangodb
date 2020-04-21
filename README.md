# docker-compose-arangodb
ArangoDB with Docker and Docker Compose

## Usage (start server)

On folder that contains `docker-compose.yml` type one of this.

```
// non detach mode
docker-compose up
```
or
```
// detach mode
docker-compose up -d
```

It will spin the ArangoDB latest version (currently 3.x.x version), expose port to host at 8529.

## Usage (stop server)

To shutdown database without remove the container.

```
docker-compose stop
```

To shutdown database and remove the container.
```
docker-compose down
```

Is data or user that already created will gone? No, since in the Docker Compose file you can see that we utilize data container named `arangodb_data_container` and `arangodb_apps_data_container` to store the ArangoDB data and apps.

## ArangoDB credential

- Username: root
- Password: rootpassword

## How to connect to ArangoDB

### Via WebUI
Go to http://localhost:8529

### Via command line
Make sure you have `arangosh` client tool command installed.

```
arangosh --server.endpoint http+tcp://127.0.0.1:8529 --server.password rootpassword
```

Enjoy your local ArangoDB database server for any purpose you want, for me this setup is fine for testing purpose.

# Redis

1. Start `Redis` via [docker-compose](https://docs.docker.com/compose/) in terminal:

  ```shell
    $ cd ./redis-docker-compose
    $ docker-compose up -d
  ```

2. Connect to the Redis server:

  ```shell
    $ docker exec -ti redis redis-cli -h 127.0.0.1 -p 6379 -a 12345678
  ```

3. Other commands maybe needed:
  ```shell
    # you can stop service by the command
    $ docker stop redis
    # you can start service by the command
    # maybe you need this command after your computer restart
    $ docker start redis
    # you can restart service by the command
    # maybe you need this command after you made some update for [redis.conf]
    $ docker restart redis
  ```

# Q&A
1. How to change password?
  * Just change the line `requirepass 12345678` in file `redis.conf` to `requirepass [new password]`, and then restart the service with command `docker restart redis`

