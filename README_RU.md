# chaiNS
[English](https://github.com/wufiry/chaiNS "Change Lang")

chaiNS - это клиент V2Ray & XRay, поддерживающий глобальный Transparent Proxy на Linux и совместимый с протоколами Blackhole, Dokodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks, VMess.

## Установка

1. #### Клонирование репозитория

	> `
git clone https://github.com/wufiry/chaiNS.git
`

2. #### Смена текущей директорию

	> `
cd ~/chaiNS/assets/
`

3. #### Файл `chains` нужно копировать в директорию ` /usr/bin `
	> ``
cp ~/chaiNS/assets/chains /usr/bin/ 
``

4. #### Создание директорию с нужными файлами.
   	Рекомендуется `~/chaiNS`

5. #### Копирование файлов в ново-созданную директорию.
	Файлы которые нужно скопировать:
   > v2ray.json
   
   > xray.json
   
   > tconfig.json

6. #### Смените `~/` в файле [xray.json](https://github.com/wufiry/chaiNS/blob/main/assets/xray.json) && [v2ray.json](https://github.com/wufiry/chaiNS/blob/main/assets/xray.json) на строке `90` на вашу домашнюю директорию.

7. #### Создайте сервис (демон) по гайду далее и перезагружайте компьютер.
	### Информация:
	#### 1. Вы должны конфигурировать “outbounds” в файле tconfig.json сами.
	#### 2. Первый старт по инструкции через сервис (демон) не запускает прокси, вы должны перезагрузить компьютер во второй раз.
	#### 3. chaiNS имеет функции. 
		
  	#### Больше информации о функциях: ` $ chaiNS --help `

## Daemons
<details>

<summary>OpenRC</summary>

### ~/chaiNS/daemons/openrc
#### Переименуйте файл на chaiNS
> Файл сервиса нужно копировать в ``/etc/init.d``

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
#### После копирования, нужно выполнить следующие команды:

```sh
chmod +x chaiNS
rc-update add chaiNS default
```
</details>

<details>

<summary>SystemD</summary>

#### ~/chaiNS/daemons/systemd.service
#### Переименуйте файл на chaiNS.service
> Файл сервиса нужно копировать в ``/etc/systemd/system/``

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
#### После копирования, выполните следующие команды:

```sh
systemctl daemon-reload
systemctl enable --now chaiNS
```
</details>

#### Тестировано на ArtixLinux c OpenRC и ArchLinux c SystemD.

## Конфигурация '' outbounds ''

<details>

<summary>V2Ray</summary>

[Гайд](https://v2ray.com/en/configuration/protocols "Choose needed protocol")

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

