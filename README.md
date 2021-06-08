# Deploy the Redis Cluster(master-slave replication) with sentinel servers.
A self-healing redis cluster setup using Ansible.
## Description
Redis cluster deployment contains two roles redis and redis-sentinel.
- [redis](https://redis.io/documentation) is used to deploy redis master and slave servers.
- [redis-sentinel](https://redis.io/topics/sentinel) is used to deploy redis sentinel servers.

Ideal cluster setup is 3 nodes for Redis (1 master, 2 slaves) and 3 nodes for Sentinel.
## Getting Started
```shell
ansible-playbook -i inventories/redis/<environment>/hosts redis-cluster.yml
```

E.G. If you are installing the redis cluster in production

```shell
ansible-playbook -i inventories/redis/production/hosts redis-cluster.yml
```
### Variables
* [ip=10.0.0.45](inventories/redis/test/hosts#L1) mentioned in the ansible inventory is set to private IP because when using public cloud services you may use [ansible_host](inventories/redis/test/hosts#L1) to configure with public IP. 
* [redis version](inventories/redis/test/group_vars/all.yml#L5) mentioned should be available to download from the [redis download page.](http://download.redis.io/releases/)
* [dns_domain](inventories/redis/test/group_vars/all.yml#L2) specify the hostname of the node VM
* [redis_port](inventories/redis/test/group_vars/all.yml#L11) variable to specify the port number Redis is listening to.
* [redis_sentinel_port](inventories/redis/test/group_vars/all.yml#L12) variable to specify the port number Sentinel is listening to.
* [redis_cluster_name](inventories/redis/test/group_vars/all.yml#L15) name of the Redis cluster
* [minimum_slaves](inventories/redis/test/group_vars/all.yml#L18) minimum number of slave nodes to be registered under the Master Node. 
* [sentinel_quorum](inventories/redis/test/group_vars/all.yml#L18) is the number of Sentinels that need to agree about the fact the master is not reachable, in order to really mark the master as failing, and eventually start a failover procedure if possible.
### Tested Versions
* CentOS Linux release 7.9.2009 (Core)
* Ansible 2.11.1
* Redis 6.2.4