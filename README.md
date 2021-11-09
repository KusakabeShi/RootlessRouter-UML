# RootlessRouter-UML

The continue of https://github.com/KusakabeSi/RootlessRouter, but use User mode linux instead of VPP  

## Node list

Here is the list of all my nodes with this architecture.  
**Please consider to peer with me if you are a [DN42](https://lantian.pub/en/article/modify-website/dn42-experimental-network-2020.lantian/) player!**  
Choose the nearest node to you, then click **Auto Peer** button to peer with me.

URL                              | Location  | Accept New Peer
---------------------------------|-------|-------|
https://dn42jpe.azurewebsites.net|Japan Tokyo| O
https://dn42ch.azurewebsites.net |Switzerland Zürich| O
https://dn42ca.azurewebsites.net |Canada Toronto| O
https://dn42au.azurewebsites.net |Australia Canberra| O
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai| O
https://dn42sg.azurewebsites.net |Singapore| X
https://dn42br.azurewebsites.net |Brazil São Paulo| X
https://dn42uk.azurewebsites.net |United Kingdom London| X
https://dn42usw.azurewebsites.net|United States California| X
https://dn42hk.azurewebsites.net |Hong Kong| X

## Node Status
https://42status.kskb.eu.org


## What is this?

DN42 is a big dynamic  VPN, which employs Internet technologies (BGP, whois database, DNS, etc) for educational and amateur scientific research purposes. Participants connect to each other using network tunnels (GRE, OpenVPN, Tinc, IPsec, Wireguard) and exchange routes thanks to the BGP. Dn42 can be used to learn networking and to connect private networks, such as hackerspaces or community networks. But above all, experimenting with routing in dn42 is fun!

The first thing we need to do is setup a router which running a BGP daemon such as BIRD/FRRouting in it. Most people choose a regular linux machine as their router. In this setup, we enable the `ip_forward` option in linux kernel to make it become a router, then the BGP daemon exahange routes with other peer and write all route tables to the kernel. Which means we need the root permission to setup all things.

But I'm thinking, do we really need that? Technically, we are just receives `wireguard encrypted udp packet` -> `decrypt it` -> `do BGP routing` -> `encrypt` -> `send to another peer`. Do we need root permission to do that? I don't think so. That's why this project here.

This `RootlessRouter` aims to build a software stack which can establish multiple wireguard sessions with other DN42 players, but all processes are done in the userspace. So that the whole stack can run as a normal user without root or in an unprivileged docker container.

## Architecture

Based on my current plan, the software stack of my nodes looks like this:
![Node](https://raw.githubusercontent.com/KusakabeSi/RootlessRouter-UML/main/pics/Node.png)

As you can see, there are no component running in the kernel mode.

I will host multiple node to form a cluster, like this
![Node](https://raw.githubusercontent.com/KusakabeSi/RootlessRouter/main/pics/Overview.png)


### Related projects:

#### Active

1. https://github.com/KusakabeSi/RootlessRouterDocker
1. https://github.com/KusakabeSi/EtherGuard-VPN
1. https://github.com/KusakabeSi/DN42-AutoPeer
1. https://github.com/KusakabeSi/slirpnetstack
1. https://github.com/KusakabeSi/bird-lg-go
1. https://github.com/KusakabeSi/UML-Config


#### Decprecated:

1. https://github.com/KusakabeSi/bird-vpp-route-syncer
1. https://github.com/KusakabeSi/wireguard-go-vpp
1. https://github.com/KusakabeSi/RootlessRouter
1. https://github.com/KusakabeSi/BIRD-vpp
1. https://github.com/KusakabeSi/vpp

#### Private:

1. https://github.com/KusakabeSi/RRstate
