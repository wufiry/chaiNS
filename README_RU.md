# chaiNS
[English](https://github.com/wufiry/chains/blob/main/README.md "Change Lang")

chaiNS - это клиент V2Ray & XRay, поддерживающий глобальный прозрачный прокси на Linux и совместимый с протоколами SS, SSR, Trojan, Tuic и Juicity.

## Установка
### OpenRC
> [chaiNS](https://github.com/wufiry/chains/blob/main/OpenRC/chaiNS "Файл программы")
>> Файл chaiNS требуется скопировать в 
```sh
/usr/local/bin \
/usr/bin
```
``sh
cp ~/Downloads/chaiNS /usr/local/bin 
``

После чего, требуется создать папку в ~/ куда будет транспортирован файл [tconfig.json](https://github.com/wufiry/chains/blob/main/OpenRC/tconfig.json "Конфиг v2ray && xray core")

### SystemD

## Daemons
### OpenRC 
> chaiNS.init
```sh
#!/sbin/openrc-run

name="chaiNS"
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
chmod +x chaiNS
rc-update add chains default
```
### SystemD
> chaiNS.service
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
ExecStart=/usr/local/bin/chaiNS
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
```sh
systemctl daemon-reload
systemctl enable --now chaiNS
```
### Протестировано на ArtixLinux OpenRC & ArchLinux SystemD

# Пожертвования

<p align="center">
<img src="https://www.crypto-news.net/wp-content/uploads/2016/09/monero.png" alt="monero" width="300" height="158"/>
</p>
	
 ### `46AEKHwWpS8cj1a5Q2sJ1ZSZ4YvmXYTkgEnnsbpeFjQZW8NQSZinASkKNwiBoX4SN3SadYLZjSEbeevnVefe696PEbJv5yU`

 <p align="center">
 <a href="https://imgbb.com/"><img src="https://i.ibb.co/QmjfP6H/photo-2024-11-21-22-45-13.jpg" alt="photo-2024-11-21-22-45-13" border="0"></a>
