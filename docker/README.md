# Build

* ```make```

# Before running

* Edit your [config.toml](https://github.com/future-architect/vuls#step6-config) to match your infrastructure
* generate a keypair dedicated to this docker : ```ssh-keygen -t rsa -b 4096 -C "your_email@example.com"```
  * it's **highly** recommanded to use a restrained `authorized_keys` files with this key to be sure that it will be only usable from a single IP (after all it's a root executed software) : ```from="1.2.3.4,1.2.3.5" ssh-rsa [...] your_email@example.com```
* Deploy your ssh key on the targetted machines

# Run

## Docker Run

```
$ docker run -it --rm -v $(pwd)/config.toml:/app/config.toml -v $(pwd)/vuls.sqlite3:/app/vuls.sqlite3 -v /path/to/id_rsa:/app/id_rsa asannou/vuls scan
[May 12 08:19:32]  INFO Opening DB. datafile: /app/cve.sqlite3
[May 12 08:19:32]  INFO Migrating DB
[May 12 08:19:32]  INFO Starting HTTP Server...
[May 12 08:19:32]  INFO Listening on 127.0.0.1:1323
INFO[0000] Start scanning (config: /app/config.toml)
[May 12 08:19:34]  INFO [localhost] Validating Config...
{"time":"2016-05-12T08:19:34Z","remote_ip":"127.0.0.1","method":"GET","uri":"/health","status":200, "latency":151,"latency_human":"151.819µs","rx_bytes":0,"tx_bytes":0}
[May 12 08:19:34]  INFO [localhost] Detecting the type of OS...
[May 12 08:19:35]  INFO [localhost] (1/1) Successfully detected. ec2: amazon 2016.03
[May 12 08:19:35]  INFO [localhost] Scanning vulnerabilities...
[May 12 08:19:35]  INFO [localhost] Check required packages for scanning...
[May 12 08:19:35]  INFO [localhost] Scanning vulnerable OS packages...
[May 12 08:19:38]  INFO [ec2:22] Fetching CVE details...
[May 12 08:19:38]  INFO [ec2:22] Done
[May 12 08:19:38]  INFO [localhost] Scanning vulnerable software specified in the CPE...
[May 12 08:19:38]  INFO [localhost] Reporting...

ec2 (amazon 2016.03)
====================
No unsecure packages.

[May 12 08:19:38]  INFO [localhost] Insert to DB...
```

## Docker Compose

* Edit docker-compose.yml
* ```docker-compose run --rm vuls```
