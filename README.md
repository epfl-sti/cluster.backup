# `cluster.backup`

A set of tools to back up precious data inside an EPFL-style CoreOS cluster

## `cluster.backup.server`

Low-tech, git-based place to push precious data into

- Access control is [capability-based](https://en.wikipedia.org/wiki/Capability-based_security) i.e. if you know the Git URL, you can freely push & pull

### Build the Docker image

```
(cd backup-server/; docker build -t epflsti/cluster.backup.server .)
```

### Run the Docker image

The low-tech (Kubernetes-less) way:

```
(cd backup-server/; docker build -t epflsti/cluster.backup.server .)
docker run --name cluster.backup.server -d -v /srv/cluster.coreos.backup/git:/git -p 9800:80 epflsti/cluster.backup.server
```

### Create secret repository

1. Create a secret token to act as the in-URL password: ```pwgen 20```
2. <pre>
(cd /srv/cluster.backup; \
 sudo mkdir -p git/puppetca-ABC123456; \
 cd git/puppetca-ABC123456;
 sudo git init --bare )
</pre>
