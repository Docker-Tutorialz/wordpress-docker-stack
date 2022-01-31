## Docker Compose - Deploying two services on Swarm

When talking about Docker in production environments, Docker Compose is mainly used, it is here in Compose that you code how your application should be deployed (services, volumes, networks). You can have n services (database, app, load balance) that Docker Compose will handle all this in a simple and organized way, that's because Compose uses YAML files and you can declaratively write your resources and thus upload your app quickly and efficiently.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install foobar
```

## Usage

To deploy the stack please proceed with the command below:

```shell
$ docker stack deploy -c docker-compose.yml wordpress
Creating network wordpress_default
Creating service wordpress_blog
Creating service wordpress_db
```

## Checkng the network

```shell
$ docker network ls
NETWORK ID     NAME                DRIVER    SCOPE
owezpbfwk750   wordpress_default   overlay   swarm
```

## Checking the services

```
$ docker service ls
ID             NAME             MODE         REPLICAS   IMAGE              PORTS
vmbkmj4rod1t   wordpress_blog   replicated   1/1        wordpress:latest   *:8082->80/tcp
m5zwzf9mrwd7   wordpress_db     replicated   1/1        mariadb:latest
```

## Checking the stack

```
$ docker stack ls
NAME        SERVICES   ORCHESTRATOR
wordpress   2          Swarm
```

## Checking the stack on nodes of Swarm

```
$ docker stack ps wordpress
ID             NAME               IMAGE              NODE       DESIRED STATE   CURRENT STATE               ERROR     PORTS
j1nk21qrvyn1   wordpress_blog.1   wordpress:latest   elliot02   Running         Running about an hour ago
3dm7g8jmlwyi   wordpress_db.1     mariadb:latest     elliot01   Running         Running about an hour ago
```

## Checkin the services on stack

```
$ docker stack services wordpress
ID             NAME             MODE         REPLICAS   IMAGE              PORTS
vmbkmj4rod1t   wordpress_blog   replicated   1/1        wordpress:latest   *:8082->80/tcp
m5zwzf9mrwd7   wordpress_db     replicated   1/1        mariadb:latest
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GNU General Public License v3.0](https://github.com/Docker-Tutorialz/wordpress-docker-stack/blob/main/LICENSE)
