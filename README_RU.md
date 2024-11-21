# chains
[English](main/README.md)

Клиент ТПрокси поддерживающий v2ray && xray ядра с чейнами от русской осинт команды - tw

## Установка
### OpenRC
> [chains](https://github.com/wufiry/chains/blob/main/chains "Файл программы")
>> Файл chains требуется скопировать в 
```sh
/usr/local/bin \
/usr/bin
```
``sh
cp ~/Downloads/chains /usr/local/bin 
``

После чего, требуется создать папку в ~/ куда будет транспортирован файл [tconfig.json](https://github.com/wufiry/chains/blob/main/tconfig.json "Конфиг v2ray && xray core")

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

[Install]
WantedBy=multi-user.target
```
```sh
systemctl daemon-reload
systemctl enable --now chains
```

# Пожертвования

### Monero XMR - []
