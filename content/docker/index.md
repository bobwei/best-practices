# Running Docker Host on AWS EC2 and Connect from Remote

* [One Script to Get Docker on Ubuntu](#one-script-to-get-docker-on-ubuntu)
* [Generate Credentials](#generate-credentials)
* [Configure Docker for Secure Connection](#configure-docker-for-secure-connection)
* [Setup Docker Client](#setup-docker-client)


#### One Script to Get Docker on Ubuntu

on Ubuntu
```
curl -fsSL https://experimental.docker.com/ | sh
```


#### Generate Credentials

```
mkdir -p ~/docker && cd ~/docker
ln -s ~/docker /var/docker
export HOSTNAME=YOUR_HOSTNAME
curl -fsSL https://gist.githubusercontent.com/bobwei/572506b2de3e35d4cabb230f10a06e07/raw/a5c0e499f71b13be69a70b2e06cb8f8708db2255/generate_docker_cert.sh | sudo sh
```

References

* [https://gist.github.com/bobwei/572506b2de3e35d4cabb230f10a06e07](https://gist.github.com/bobwei/572506b2de3e35d4cabb230f10a06e07)


#### Configure Docker for Secure Connection

The following config setup docker deamon to listen on 0.0.0.0:2376 and use given ca, cert and key to verify client

```
# Use DOCKER_OPTS to modify the daemon startup options.
DOCKER_OPTS="-D --dns 8.8.8.8 --dns 8.8.4.4 -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock --tlsverify --tlscacert=/var/docker/ca.pem --tlscert=/var/docker/server-cert.pem --tlskey=/var/docker/server-key.pem"
```

References

* [docker config example](./docker_config)
* [Protect the Docker daemon socket](https://docs.docker.com/engine/security/https/)


#### Setup Docker Client

download certificates and keys from docker host
```
scp -i ~/.ssh/your_key -r ubuntu@HOSTNAME:~/docker ~/.docker/HOSTNAME
```

setup env for devmachine
```
export DOCKER_HOST=tcp://HOSTNAME:2376
export DOCKER_CERT_PATH=~/.docker/HOSTNAME
export DOCKER_TLS_VERIFY=1
```

Finally, you can operate with docker commands
```
docker ps
```
