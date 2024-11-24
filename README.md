# chaiNS
[Русский](https://github.com/wufiry/chaiNS/blob/main/README_RU.md "Сменить Язык")

chaiNS is a V2Ray && XRay client supporting global transparent proxy on Linux and  it is compatible with Blackhole, Dokodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks, VMess.

## Download

1. #### Cloning repository

	> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Change the current directory

	> `
cd ~/chaiNS/assets/
`

3. #### The file `chains` needs to be copied to ` /usr/bin `
	> ``
cp ~/chaiNS/assets/chains /usr/bin/ 
``

4. #### Create the config directory.
	Recommended name and location `~/chaiNS`

5. #### Copying files to a newly created directory.
	Files:
   > v2ray.json
   
   > xray.json
   
   > tconfig.json

6. #### Create the daemon and reboot
	### Info:
	#### 1. You must configure the “outbounds” yourself in the tconfig.json file
	#### 2. The first run following the instructions with the daemon will not start the proxy, you will have to second reboot
	#### 3. The chaiNS has commands. 
		
  	#### More info: ` $ chaiNS --help `

## Daemons
<details>

<summary>OpenRC</summary>

### ~/chaiNS/daemons/openrc
#### Rename the file to chaiNS
> The service file should be copied to ``/etc/init.d``.

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

#### ~/chaiNS/daemons/systemd.service
#### Rename the service to chaiNS.service
> Needed copy service file to ``/etc/systemd/system/``

```sh
[Unit]
Description=A transparent proxt v2ray&xray chains client
Documentation=https://github.com/wufiry/chaiNS
After=network.target nss-lookup.target iptables.service ip6tables.service nftables.service xray.ser>
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
#### After copy service file, the next commands must be executed

```sh
systemctl daemon-reload
systemctl enable --now chaiNS
```
</details>

#### Tested on ArtixLinux OpenRC & ArchLinux SystemD

## Configuration '' outbounds ''

<details>

<summary>V2Ray</summary>

[V2Ray Configuration Guide](https://v2ray.com/en/configuration/protocols "Choose needed protocol")

</details>

<details>

<summary>XRay</summary>

[XRay Configuration Guide](https://xtls.github.io/en/config/outbounds/blackhole.html "Look for the rest of the protocols in the tree on the left")

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

 
