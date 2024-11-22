# chaiNS
[English](https://github.com/wufiry/chaiNS "Change Lang")

chaiNS - это клиент V2Ray & XRay, поддерживающий глобальный Transparent Proxy на Linux и совместимый с протоколами Blackhole, Dokodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks, VMess.

## Установка
<details>

<summary>OpenRC</summary>

1. #### Клонирование репозитория

> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Смените текущую директорию

> `
cd ~/chaiNS/OpenRC
`

3. #### Файл ` chains ` требуется скопировать в ` /usr/bin `
> ``
cp ~/OpenRC/chains /usr/bin 
``


</details>
<details>

<summary>SystemD</summary>

1. #### Клонирование репозитория

> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Смените текущую директорию

> `
cd ~/chaiNS/SystemD
`

</details>

## Daemons

<details>

<summary>OpenRC</summary>

### ~/chaiNS/OpenRC/chaiNS.init

#### Необходимо удалить расширение файла сервиса OpenRC.

#### Необходимо скопировать файл сервиса в директорию `` /etc/init.d/ ``

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
#### После копирования, требуется выполнить следующие команды:

```sh
chmod +x chaiNS
rc-update add chaiNS default
```
</details>

<details>

<summary>SystemD</summary>

### ~/chaiNS/SystemD/chaiNS.service
> Необходимо скопировать файл сервиса

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

#### Протестировано на ArtixLinux OpenRC & ArchLinux SystemD

## Конфигурация chaiNS

<details>

<summary>V2Ray</summary>

[Документация по конфигурации V2Ray](https://v2ray.com/ru/configuration/protocols "Выберите нужный протокол")

</details>

<details>

<summary>XRay</summary>

[Документация по конфигурации XRay](https://xtls.github.io/en/config/outbounds/blackhole.html "Остальные протоколы ищите в дереве слева")

</details>

# Пожертвования

<p align="center">
<img src="https://www.crypto-news.net/wp-content/uploads/2016/09/monero.png" alt="monero" width="150" height="79"/>
</p>
	
 ### `46AEKHwWpS8cj1a5Q2sJ1ZSZ4YvmXYTkgEnnsbpeFjQZW8NQSZinASkKNwiBoX4SN3SadYLZjSEbeevnVefe696PEbJv5yU`

 <p align="center">
 <img src="https://cdn.icon-icons.com/icons2/2699/PNG/512/litecoin_logo_icon_170221.png" alt="litecoin" width="150" height="79" />
 </p>

 ### `LNQHtC6vEdqCzhihtNYBLQjNW27GP4Uo8o`

