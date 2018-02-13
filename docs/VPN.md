This guide uses NordVPN as an example though there are many other VPN Providers.

### Install Dependencies

```
sudo apt-get update
sudo apt-get install openvpn
sudo apt-get install unzip
```

### Install NordVPN server configs

```
cd /etc/openvpn/ 
sudo wget https://nordvpn.com/api/files/zip
sudo unzip zip
```

### Connect to VPN

`sudo openvpn file_name` (for example: sudo openvpn de75.nordvpn.com.udp1194.ovpn)

To Kill Process: `Ctrl+C` or `sudo killall openvpn`

### Start VPN at Boot

TODO