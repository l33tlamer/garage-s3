# Garage S3

A very basic example of [Garage](https://garagehq.deuxfleurs.fr/) for S3 storage.

The config file `garage.toml` needs to exist before you bring up the container.

Replace `192.168.100.200` with whatever "public" IP your Docker host is using.

Generate your own tokens with `openssl rand -hex 32`.

See the Garage documentation for details:

* https://garagehq.deuxfleurs.fr/documentation/quick-start/

In the compose, modify the metadata and data volumes to suit your setup.

Once you have the container running, having a alias in your shell makes things easier:

`alias garage='docker exec -it garage /garage'`

Then here are some basic commands:

```
garage status
garage layout assign FIRSTDIGITSOFNODEID -z ZONENAME -c 10 -t NODETAG
garage layout show
garage layout apply --version 1
garage status

garage bucket create BUCKETNAME
garage bucket list
garage bucket info BUCKETNAME

garage key new --name KEYNAME
garage key list
garage key info KEYNAME

garage bucket allow --read --write --owner BUCKETNAME --key KEYNAME
garage bucket info BUCKETNAME
```
