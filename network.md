add br0

```
sudo nmcli con add type bridge ifname br0
sudo nmcli con modify bridge-br0 bridge.stp no
sudo nmcli con modify bridge-br0 ipv4.method manual ipv4.address 192.168.100.100/32
sudo nmcli c down bridge-br0 && sudo nmcli c up bridge-br0
```

add br1

```
sudo nmcli con add type bridge ifname br1
sudo nmcli con modify bridge-br1 bridge.stp no
sudo nmcli con modify bridge-br1 ipv4.method manual ipv4.address 192.168.100.101/32
sudo nmcli c down bridge-br1 && sudo nmcli c up bridge-br1
```

network status
```
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:d9:91:58 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.51/24 brd 192.168.122.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::9573:69d0:16b4:2393/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:21:7e:76 brd ff:ff:ff:ff:ff:ff
    inet 10.111.0.51/16 brd 10.111.255.255 scope global noprefixroute eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::e6ff:8e63:9ffd:7962/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: br1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 82:43:3e:2b:46:a6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.101/32 brd 192.168.100.101 scope global noprefixroute br1
       valid_lft forever preferred_lft forever
5: br0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether b2:fd:06:de:9d:85 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.100/32 brd 192.168.100.100 scope global noprefixroute br0
       valid_lft forever preferred_lft forever
```

   