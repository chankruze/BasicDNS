
### Introduction

BasicDNS is a very simple DNS server.
It was made to learn the basics of the DNS protocol.

Features:
* very small
* single-threaded
* all necessary data structures for further features
* very simplistic memory management
* no full protection against malformed requests :|

### Build

```
git clone https://github.com/chankruze/BasicDNS.git
cd BasicDNS
make
```

### Test

Start BasicDNS:
```
$./main
Listening on port 9000.
```

In another console execute [dig](http://linux.die.net/man/1/dig) to make a DNS request:

```
$ dig @127.0.0.1 -p 9000 geekofia.com A

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @127.0.0.1 -p 9000 geekofia.com A
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24053
;; flags: qr; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;geekofia.com.			IN	A

;; ANSWER SECTION:
geekofia.com.		235929600 IN	A	192.168.1.1

;; Query time: 0 msec
;; SERVER: 127.0.0.1#9000(127.0.0.1)
;; WHEN: Mon Oct 15 20:33:54 IST 2018
;; MSG SIZE  rcvd: 58
```

Note:
- On Debian Linux, dig is part of the dnsutils package.
- Use AAAA instead of A in the dig command line to request the IPv6 address.

## Modify address entries

The code maps the domain "geekofia.com" to the IPv4 address 192.168.1.1 and IPv6 address fe80::1.
It is easy to find it in the code and to add other entries.

### Recommended Reading

The DNS section of the [TCP/IP-Guide](http://www.tcpipguide.com/free/t_TCPIPDomainNameSystemDNS.htm) was very helpful for understanding the protocol.
