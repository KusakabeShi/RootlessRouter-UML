# RootlessRouter-UML

The continue of https://github.com/KusakabeSi/RootlessRouter, but use User mode linux instead of VPP  

## Node list

Here is the list of all my nodes with this architecture.  
**Please consider to peer with me if you are a DN42 player!**  
Choose the nearest node to you, then click **Peer with me** button in the top left corner to peer with me.

URL                              | Location  | 
---------------------------------|-------|
https://dn42jpe.azurewebsites.net|Japan Tokyo
https://dn42sg.azurewebsites.net |Singapore
https://dn42ch.azurewebsites.net |Switzerland Zürich
https://dn42uk.azurewebsites.net |United Kingdom London
https://dn42usw.azurewebsites.net|United States California
https://dn42ca.azurewebsites.net |Canada Toronto
https://dn42au.azurewebsites.net |Australia Canberra
https://dn42br.azurewebsites.net |Brazil São Paulo
https://dn42uae.azurewebsites.net|United Arab Emirates Dubai
https://dn42hk.azurewebsites.net |Hong Kong(Not ready for peer)

## Node Status
https://42status.kskb.eu.org

## Architecture

This router can establish multiple wireguard sessions with other DN42 players, but all the tasks can run as a normal user without root / in an unprivileged docker container.
The program receives `wireguard encrypted udp packet` -> `decrypt it` -> `do bgp routing` -> `encrypt` -> `send to another peer`, all processes are done in the userspace.

The host OS can only see this app receives and sends udp packets, but don't know it established multiple BGP sessions to other people and routing for it.

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
