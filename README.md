# chaiNS
[Русский](https://github.com/wufiry/chaiNS/blob/main/README_RU.md "Сменить Язык")

chaiNS is a V2Ray && XRay client supporting global transparent proxy on Linux and  it is compatible with Blackhole, Dokodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks, VMess.

## Download
<details>

<summary>OpenRC</summary>

1. #### Cloning repository

> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Change the current directory

> `
cd ~/chaiNS/OpenRC
`

3. #### The file `chains` needs to be copied to ` /usr/bin `
> ``
cp ~/OpenRC/chains /usr/bin 
``


</details>
<details>

<summary>SystemD</summary>

1. #### Cloning repository

> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Change the current directory
> `
cd ~/chaiNS/SystemD
`

</details>

## Daemons
<details>

<summary>OpenRC</summary>

### ~/chaiNS/OpenRC/chaiNS.init

#### It is necessary to remove the file extension of the OpenRC service.

#### It is necessary to copy the service file to the directory `` /etc/init.d/ ``

> ` cp chaiNS /etc/init.d `

```sh
#!/sbin/openrc-run

name="chaiNS"
description="A transparent proxy v2ray/xray chains client by ru osint team - tw"
command="/usr/bin/chains"
pidfile="/run/${RC_SVCNAME}.pid"
command_background="yes"
rc_ulimit="-n 30000"
rc_cgroup_cleanup="yes"

 depend() {
	need net
	after net
   }
```
#### After copy service file, the next commands must be executed

```sh
chmod +x chaiNS
rc-update add chaiNS default
```
</details>

<details>

<summary>SystemD</summary>

### ~/chaiNS/SystemD/chaiNS.service
> Needed copy service file to

```sh
[Unit]
Description=A transparent proxy v2ray/xray chains client by ru osint team - tw
Documentation=https://github.com/wufiry/chaiNS
After=network.target nss-lookup.target iptables.service ip6tables.service nftables.service
Wants=network.target

[Service]
Type=simple
User=root
LimitNPROC=500
LimitNOFILE=1000000
ExecStart=/usr/bin/chains
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
```sh
systemctl daemon-reload
systemctl enable --now chaiNS
```
</details>

#### Tested on ArtixLinux OpenRC & ArchLinux SystemD

## Configuration chaiNS

<details>

<summary>V2Ray</summary>

[V2Ray Configuration Guide](https://v2ray.com/en/configuration/protocols "Choose needed protocol")

</details>

<details>

<summary>XRay</summary>

[XRay Configuration Guide](https://xtls.github.io/en/config/outbounds/blackhole.html "Look for the rest of the protocols in the tree on the left")

</details>

### Commands

<details>

<summary>Commands</summary>

> $ chaiNS -h
                     
>> print commands
                      
> $ chaiNS --help

> $ chaiNS -r
                     
>> restart daemon after change config chaines for use them
                      
> $ chaiNS --restart

</details>

# Donate

<p align="center">
<img src="https://www.crypto-news.net/wp-content/uploads/2016/09/monero.png" alt="monero" width="150" height="79"/>
</p>
	
 ### `46AEKHwWpS8cj1a5Q2sJ1ZSZ4YvmXYTkgEnnsbpeFjQZW8NQSZinASkKNwiBoX4SN3SadYLZjSEbeevnVefe696PEbJv5yU`

 <p align="center">
 <img src="https://cdn.icon-icons.com/icons2/2699/PNG/512/litecoin_logo_icon_170221.png" alt="litecoin" width="150" height="79" />
 </p>

 ### `LNQHtC6vEdqCzhihtNYBLQjNW27GP4Uo8o`

 
