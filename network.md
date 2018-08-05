## Network

- `ifconfig`
- `route`
- `ping -c 3 localhost`

The agency assigns Internet service providers (ISPs) one or more blocks of IP
addresses, which the ISPs can then assign to their subscribers.


##

- `ethtool eth0`
- `ethtool -i eth0` driver information

- `netstat -i -c` network statistics
- `netstat -tanp` TCP trafic only

- `dig bioinformatics.erc.monash.edu` DNS look up

- `arp -v`

- `traceroute bioinformatics.erc.monash.edu`
- `traceroute -n bioinformatics.erc.monash.edu`

- `tracepath bioinformatics.erc.monash.edu`

- `tcpdump` dumps network traffic

##

[biostation2]~$ tcpdump -n 'port not 22 and not arp'


##

- `route -n` shows my routing table
- `arp -n` get mac address of machine that you're trying to talk to,
before you can talk to it, you need to `ping` it `ping 130.194.109.33`

There is a difference between my local area netwrok and outside. For my machine to
talk to the outside it needs to go via gateway, use `routne -n` to see my gateway

nmap
ifconfig
arp -n
ping 130.194.108.33
arp -n
route -n

mtr
traceroute

traceroute 130.194.108.33
traceroute 130.194.109.33

- `mtr`
