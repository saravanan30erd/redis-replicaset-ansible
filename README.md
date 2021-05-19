### Deploy the Redis Cluster(master-slave replication) with sentinel servers.
    
Redis cluster deployment contains two roles redis and redis-sentinel.
- redis is used to deploy redis master and slave servers.
- redis-sentinel is used to deploy redis sentinel servers.
    
```shell
ansible-playbook -i inventories/redis/<environment>/hosts redis-cluster.yml
```

E.G. If you are installing the redis cluster in production,

```shell
ansible-playbook -i inventories/redis/production/hosts redis-cluster.yml
```