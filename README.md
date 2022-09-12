# WireGuard installer for Gaming

**This project is a bash script that aims to setup a [WireGuard](https://www.wireguard.com/) VPN that is specified for PERSONAL gaming or torrenting use. It supports only ONE client!**

If you are looking for a common WireGuard install script that supports multi-client connections, i.e. multiple devices connect to the VPN at the same time, please visit [this repository](https://github.com/angristan/wireguard-install/) to continue.

The script **Port Forwards** the local port 1-65500` to the corresponding ports on the server side. These ports covered most of the ports used by any games. **Please make sure that there is no other application using these ports on the server, otherwise It will deafen any application that listens to these ports.** I highly suggest running this script on an new empty system. 

Specifically, the script will move ssh to port `65522` for not losing access to the server after installation.

The script supports both IPv4 and IPv6, but its preferred to use ipv4 as connection to the server.

## NAT Improvement

With this script, you do not need to enable port forwarding on your router, you do not need the DMZ setting. All the magic happens inside Wireguard. Simply speaking: 

>The local ports will be forwarded to the server directly.

It solves the following scenarios:

1. You want to host a Minecraft/Terraria, etc. server online and play with your friend, but you cannot figure out how to enable port forwarding on your router, or your ISP just did not give you a public IP address.

2. You play a P2P game like Monster Hunter: World or Overcooked! but your NAT type prevents you from connecting with other players. 

For a better gaming experience, the server should be close to your living region and has a low ping value. You should ping the provider's looking glass datacenter IP first before purchasing a VPS.

## For Advance User

The reason why it is full cone is due to the DNAT route rules in the iptables:


If the game needs port that is not covered inside, you can modify the postup and postdown script yourself to add a certain port for it.
 
## Requirements

Supported distributions:

- Ubuntu >= 16.04
- Debian

## Usage

Download and execute the script. Answer the questions asked by the script and it will take care of the rest. For most VPS providers, you can just enter through all the questions.

```bash
wget https://raw.githubusercontent.com/Brazzo978/wg_gaming_installer/main/wg-gaming-installer.sh 
bash ./wg-gaming-installer.sh
```

It will install WireGuard (kernel module and tools) on the server, configure it, create a systemd service and a client configuration file.

## Stop / Restart / Uninstal

Run the script again will give you these options!
