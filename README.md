# Deploy the Redis Cluster(master-slave replication) with sentinel servers.
A self-healing redis cluster setup using Ansible.
## Description
Redis cluster deployment contains two roles redis and redis-sentinel.
- [redis](https://redis.io/documentation) is used to deploy redis master and slave servers.
- [redis-sentinel](https://redis.io/topics/sentinel) is used to deploy redis sentinel servers.

## Getting Started
```shell
ansible-playbook -i inventories/redis/<environment>/hosts redis-cluster.yml
```

E.G. If you are installing the redis cluster in production

```shell
ansible-playbook -i inventories/redis/production/hosts redis-cluster.yml
```
### More Info
* [ip=10.0.0.45](inventories/redis/test/hosts#L1) mentioned in the ansible inventory is set to private IP because when using public cloud services you may use [ansible_host](inventories/redis/test/hosts#L1) to configure with public IP. 
* Ideal cluster setup is 3 nodes for Redis (1 master, 2 slaves) and 3 nodes for Sentinel.
* Ensure the [redis version](inventories/redis/test/group_vars/all.yml#L5) mentioned should be available to download from the [redis download page.](http://download.redis.io/releases/)

### Tested Versions
* CentOS Linux release 7.9.2009 (Core)
* Ansible 2.11.1
* Redis 6.2.4