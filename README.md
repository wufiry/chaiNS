# chains
[Русский](https://github.com/wufiry/chains/blob/main/README_RU.md "Сменить Язык")

A transparent proxy v2ray/xray chains client by ru osint team - tw


## Download
### OpenRC
> [chains](https://github.com/wufiry/chains/blob/main/OpenRC/chains "Programm File")
>> The chains file needs to be copied to
```sh
/usr/local/bin \
/usr/bin
```
``sh
cp ~/Downloads/chains /usr/local/bin 
``

After that, you need to create a folder in ~/ where the file will be transported [tconfig.json](https://github.com/wufiry/chains/blob/main/tconfig.json "Config v2ray & xray core")
### SystemD

## Daemons
### OpenRC 
> chains.init
```sh
#!/sbin/openrc-run

name="chains"
description="A transparent proxy v2ray/xray chains client by ru osint team - tw"
command="/usr/local/bin/chains"
pidfile="/run/${RC_SVCNAME}.pid"
command_background="yes"
rc_ulimit="-n 30000"
rc_cgroup_cleanup="yes"

 depend() {
	need net
	after net
   }
```
```sh
chmod +x chains
rc-update add chains default
```
### SystemD
> chains.service
```sh
[Unit]
Description=A transparent proxy v2ray/xray chains client by ru osint team - tw
Documentation=https://github.com/wufiry/chains
After=network.target nss-lookup.target iptables.service ip6tables.service nftables.service
Wants=network.target

[Service]
Type=simple
User=root
LimitNPROC=500
LimitNOFILE=1000000
ExecStart=/usr/local/bin/chains
Restart=on-failure
```
```sh
systemctl daemon-reload
systemctl enable --now chains
```
