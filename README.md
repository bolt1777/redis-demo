# Redis Sentinel with Vagrant

## Installation

```bash
git clone https://github.com/dmarych/vagrant-redis-demo.git
cd vagrant-redis-demo
vagrant up
```

## Notes
To get state of redis, run this
```bash
vagrant ssh redis0 -c "redis-cli -p 26379 info sentinel"
