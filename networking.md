## Networking

test a webserver with http
```bash
curl -I http://example.com # -I zeigt nur den Http-Header an
```

test a webserver with https
```bash
curl -I https://192.0.0.1 # -I zeigt nur den Http-Header an
```
test a webserver on port 80 , if succesfull, a input terminal opens
telnet does not provide safety
```bash
telnet 194.164.52.55 80 # wenn erfolgreich, zeigt eingabeterminal an
```

investigate sockets
t=tcp-sockets
a=display listenting and non-listening
p=show process using socket
n=numeric, do not try to resolve service names
```bash
ss -tapn
```

show external network interface
```bash
ip route get 8.8.8.8
```

example output, ens6 is the name of the interface
```bash
8.8.8.8 via 218.134.247.8 dev ens6 src 218.134.247.8 uid 0 cache
```

show network interfaces
```bash
ifconfig
```

monitor tcp activity on a network interface
```bash
sudo tcpdump -i <network_interface_name> 
```
