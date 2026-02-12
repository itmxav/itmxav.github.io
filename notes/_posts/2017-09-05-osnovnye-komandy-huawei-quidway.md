---
id: 72
title: 'Основные команды Huawei Quidway. Сравнение с Cisco'
date: '2017-09-05T21:35:11+03:00'
author: МXAV
excerpt: ''
layout: post
guid: 'https://it.m-notes.ru/?p=72'
permalink: /2017/09/05/osnovnye-komandy-huawei-quidway/
views:
    - '33008'
ytrssenabled_meta_value:
    - 'no'
ytremove_meta_value:
    - 'no'
ytad1meta:
    - enabled
ytad2meta:
    - enabled
ytad3meta:
    - enabled
ytad4meta:
    - enabled
ytad5meta:
    - enabled
template_meta:
    - 'no'
ytextendedhtmlmeta:
    - default
ytpostdatemeta:
    - default
image: /wp-content/uploads/2017/09/switch-35568_640.png
categories:
    - 'Записи по Huawei'
tags:
    - huawei
    - сети
format: false
---

**Некоторые часто используемые команды Huawei:**\[code lang="plain"\]system-view - привелегированый режим save – запись текущих настроек в энергонезависимую память устройства; undo - отмена команды display this - показ текущей конфигурации display current-configuration – вывод текущего файла конфигурации quit - выход\[/code\] **Создание vlan**\[code lang="plain"\]vlan 1 description примечание для пользователей quit vlan 2 description для управления management-vlan quit vlan 3 description супервлан supervlan aggregate-vlan access-vlan 1 2 management-vlan quit\[/code\] **Добавление интерфейса в vlan**\[code lang="plain"\]interface Vlanif 1 ip address 192.168.1.2 255.255.255.0 quit\[/code\] **Маршрут по умолчанию**\[code lang="plain"\]ip route 0.0.0.0 0.0.0.0 192.168.1.1\[/code\] **SNMP**Настройка SNMPv2: \[code lang="plain"\]snmp-agent snmp-agent sys-info version v2c snmp community read КОМЬЮНИТИ\[/code\] **Чтобы принимались простые community введем команду:**\[code lang="plain"\]snmp-agent community complexity-check disable\[/code\] **Http**\[code lang="plain"\]http secure-server enable http server enable display http server\[/code\] Если возникнет ошибка «Error: Starting the HTTP server failed.«, то значит не загружен web пакет, который является web-интерфейсом (http сервером). Посмотрим какие есть файлы в памяти коммутатора следующей командой (нам нужен файл заканчивающийся расширением .web.zip): \[code lang="plain"\]dir\[/code\] Если файла нету, то его необходимо закачать в память коммутатора. Когда он будет находится в памяти коммутатора, запустим его командой: \[code lang="plain"\]http server load flash:/имя\_файла.web.zip\[/code\] Теперь включим его командами: \[code lang="plain"\]http secure-server enable http server enable http secure-server ssl-policy 1\[/code\] Далее рассмотрим сопоставление Cisco команды Huawei. **Ниже таблица аналогов CISCO-вских команд у HUAWEI. Huawei команды Cisco:** | **CISCO | **HUAWEI |
|---|---|
| ping | ping |
| traceroute | tracert |
| show | display |
| show interfaces | display interface |
| Show ip route | display routing-table |
| Show ip interface | Display ip interface |
| Show version | Display version |
| Show ip bgp | Display bgp routing-table |
| Show clock | Display clock |
| Show port | Display port-mapping |
| Show flash | dir flash: (on user view mode) |
| Show logging | Display logbuffer |
| Show snmp | Display snmp-agent statistics |
| Show frame-relay pvc | Display fr pvc-info |
| Show users | Display users |
| Show terminal length | screen-length disable |
|  | undo screen-length disable |
| enable | Super |
| disable | Super 0 (number is privilege level from 0 to 3, where 3 is default and equivalent to “enable” on Cisco) |
| Conf t | System-view |
| exit | quit |
| end | return |
| Show policy-map interface | Display qos policy interface |
| send | send (on user view mode) |
| write terminal (sh run) | display current-configuration |
| Sh startup | Display saved-configuration |
| \[no equivalent: shows the files used for startup\] | Display startup |
| Write erase | Reset saved-configuration |
| Write mem (or wr or copy run start) | save |
| clear counters | reset (on user view mode) |
|  | Reset counters interface |
| ? | ? |
| telnet | telnet |
| Enable secret (conf mode) | Super pass cipher (system mode) |
| Term mon | term debu |
| clock | clock |
| no | undo |
| debug / no debug | debugging / undo debugging |
| copy running-config | Save safely |
| terminal monitor | terminal monitor |
| terminal length | screen-length disable |
|  | undo screen-length disable |
| terminal no monitor | undo terminal monitor |
| clear counters | reset counters interface |
| clear interface | reset counters interface |
| clear crypto | ipsec sa |
|  | ike sa |
| clear access-list counters | reset acl counter all |
| reload | reboot |
| shutdown | shutdown |
| boot | boot bootrom |
| Aaa | hwtacacs scheme |
| terminal no monitor | undo terminal monitor |
| tacacs-server | hwtacacs scheme (in conf command) |
| snmp-server | tftp-server (in conf command) |
| router bgp | bgp |
| Router rip | rip |
| ip tacacs | hwtacacs nas-ip (this command doesn’t exist !!!) |
| mtu | Mtu (this command doesn’t exist !!!) |
| clear ip cef | reset ip fast-forwarding |
| clear ip route \* | reset ip routing-table statistics protocol all |
| Clear ip bgp | Reset bgp all |
| Show tech | display diagnostic-information |
| Sh ip nat translation | Display nat session |
| Show Controller | display controller (but not relevant for non-modular chassis) |
| show dsl int atm 0 | display dsl status interface Atm 2/0 |
| sho atm pvc | Display atm pvc-info |
| debug pvc nego | Debug atm all (very dangerous – might crash router) |
| sho crypto isakmp sa | Display ike sa |
| sho crypto isakmp key | Display ike peer |
| sho crypto isakmp police | Display ike proposal |

Источники: [Раз - ixnfo.com](http://ixnfo.com/nastroyka-kommutatora-huawei-quidway-s2326tp-ei.html)[Два - ixnfo.com](http://ixnfo.com/kak-vklyuchit-web-interfeys-na-kommutatorah-huawei-quidway.html)[Три - tokarchuk.ru](http://tokarchuk.ru/2016/02/huawei-switches-setup/)