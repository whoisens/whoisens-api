# Environment setup


### First run

```bash
docker run -dit -p 127.0.0.3:80:80 -p 127.0.0.3:443:443 --name whoisens-api whoisens-api
```


**/etc/rc.local**

```bash
sysctl -w net.ipv4.conf.all.route_localnet=1

# website
iptables -t nat -I PREROUTING -d 185.244.128.121 -p tcp --dport 80 -j DNAT --to 127.0.0.3:80
iptables -t nat -I PREROUTING -d 185.244.128.121 -p tcp --dport 443 -j DNAT --to 127.0.0.3:443

docker start whoisens-api
```