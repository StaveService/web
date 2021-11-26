# WEB

```sh
git clone https://github.com/StaveService/web.git --recursive
```

## Git Submodules

-[back](https://github.com/StaveService/back)
-[front](https://github.com/StaveService/front)

## GCE SetUp

1. [Docker Install](https://docs.docker.com/engine/install/debian/)

2. [Docker Compose Install](https://docs.docker.com/compose/install/)

3. [Docker non-root user](https://docs.docker.com/engine/install/linux-postinstall/)

   - sudo usermod -aG docker runner (github actions)

4. Git Permission

```sh
sudo groupadd web

sudo gpasswd -a izszzz_iz web

sudo gpasswd -a runner web

chgrp web /usr/local/workdir
```

5. Make Directory

```sh
sudo mkdir /home/web/back/tmp/pids
sudo mkdir /home/web/back/tmp/log
sudo mkdir /home/web/back/tmp/sockets
```

6. Set Secret File

   - master.key

7. Create DB

```sh
docker-compose -f docker-compose.yml -f docker-compose.prod.yml run back rails db:create
```

8. Up

```sh
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```
