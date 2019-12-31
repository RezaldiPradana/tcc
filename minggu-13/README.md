 ## Praktikum Teknologi Cloud

### Pertemuan 13

##### Laurentius Rezaldi Pradana Putra / 175410043
 
 1. Pertama-tama anda perlu inisialisasi docker swarm 
```
$ sudo docker  swarm init --advertise-addr 10.55.1.1
Swarm initialized: current node (ilebwnekgymz3vxf5xsx9uz76) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-1urvjhskyxd1xppwgzk8o6j4g2vruie95irkivo737yt3sfj0u-dnqcczzve27iueyxg4y75yhyj 10.55.1.1:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

```


2. Silahkan lakukan join ke swarm
```
$ docker swarm join --token SWMTKN-1-1urvjhskyxd1xppwgzk8o6j4h2dr5irkivo737yt3sfj0u-dnqcczzve27iueyxg4y75yhyj 10.55.1.1:2377
This node joined a swarm as a worker.
```

3. Lakukan deploy stack ke swarm anda.
```
$ sudo docker stack deploy --compose-file docker-compose.yml stackdemo
Ignoring unsupported options: restart

Creating network stackdemo_default
Creating service stackdemo_drupal
Creating service stackdemo_postgres
```
4. Cek running services
```
$ sudo docker stack services stackdemo
ID                  NAME                 MODE                REPLICAS            IMAGE               PORTS
c7pzxo7go4oz        stackdemo_drupal     replicated          0/1                 drupal:latest       *:8088->80/tcp
qfnqoxe24qaw        stackdemo_postgres   replicated          0/1                 postgres:10         *:5432->5432/tcp
```