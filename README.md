Deluge + OpenVPN + Privoxy
==========================

Deluge - http://deluge-torrent.org/

OpenVPN - https://openvpn.net/

Privoxy - http://www.privoxy.org/

Latest stable Deluge release for Arch Linux, including OpenVPN to tunnel torrent traffic securely (using iptables to block any traffic not bound for tunnel). This now also includes Privoxy to allow unfiltered http|https traffic via VPN.

**Pull image**

```
docker pull binhex/arch-delugevpn
```

**Run container**

```
docker run -d --cap-add=NET_ADMIN -p 8112:8112 -p 8118:8118 --name=<container name> -v <path for data files>:/data -v <path for config files>:/config -v /etc/localtime:/etc/localtime:ro -e PIA_USER=<pia username> -e PIA_PASS=<pia password> -e PIA_REMOTE=<pia remote gateway> -e ENABLE_PRIVOXY=<yes|no> binhex/arch-delugevpn
```

Please replace all user variables in the above command defined by <> with the correct values.

**Access Deluge**

```
http://<host ip>:8112
```

Default password for the webui is "deluge"

**Access Privoxy**

```
<host ip>:8118
```

Default is no authentication required

**IMPORTANT**

This Docker relies on a VPN connection to PIA (PrivateInternetAccess), please sign-up and enter your credentials in the above run command. The environment variable PIA_REMOTE allows you to define the country you want the tunnel connected to, choices are:- UK London, UK Southampton, US California, US East, US Florida, US Midwest, US Seattle, US Texas, US West, Australia, CA North York, CA Toronto, France, Germany, Hong Kong, Israel, Japan, Netherlands, Romania, Sweden, Switzerland.

