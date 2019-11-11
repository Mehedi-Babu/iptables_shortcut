# iptables Cheatsheet
Reference guide for iptables.

## Current iptables Ruleset

**Check current iptables ruleset**
```shell
sudo iptables -S
```

```shell
sudo iptables -L -v
```

## Enable Traffic on Localhost
Allow communication between applications and databases on the server.

```shell
sudo iptables -A INPUT -lo -j ACCEPT
```

## Enable Connections on HTTP, SSH, SSL
Allow regular connections to continue as usual.
```shell
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

## Filter Packets Based on Source
Allow packets from a source
```shell
sudo iptables -A INPUT -s 192.168.1.213 -j ACCEPT
```

Reject packets from a source
```shell
sudo iptables -A INPUT -s 192.168.1.213 -j DROP
```

## Drop All Other Traffic
```shell
sudo iptables -A INPUT -j DROP
```

## Delete Rules
Remove all rules withe the flush command.
```shell
sudo iptables -F
```

## Persisting Changes
To make changes persistent after reboot save the rules using the following command:

```shell
sudo /sbin/iptables-save
```

## Disable Firewall
**Flush all the rules and make changes persistent**
```shell
sudo iptables -F
sudo /sbin/iptables-save
```