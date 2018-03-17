# `cluster.backup`

A set of tools to back up precious data inside an EPFL-style CoreOS cluster

## `cluster.backup.server`

Low-tech, git-based place to push precious data into

- Access control is [capability-based](https://en.wikipedia.org/wiki/Capability-based_security) i.e. if you know the Git URL, you can freely push & pull
