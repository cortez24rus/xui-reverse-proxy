# XUI-REVERSE-PROXY

-----

### Прокси с использованием протоколов Trojan и VLESS (Reality) за реверс-прокси NGINX
Данный скрипт предназначен для полной настройки скрытого прокси-сервера с маскировкой при помощи NGINX. При данном методе настройки все запросы к прокси принимает NGINX, а сервер работает как прокси только при наличии в запросе правильного пути.

> [!IMPORTANT]
> Проверено на ОС: Debian 12, виртуализация — KVM. Для настройки понадобится свой домен, прикреплённый к аккаунту Cloudflare. Запускайте от имени root на свежеустановленной системе. Рекомендуется обновить систему и перезагрузить сервер перед запуском скрипта.
>
> Необходимо подключить домен к cloudflare, добавить DNS записи:
>
> A | domain_name | ip address | Proxied
> 
> CNAME | www | domain_name | DNS only
>
> SSL/TLS > Overview > Configure > Full
>
> SSL/TLS > Edge Cerificates > Minimum TLS Version (TLS 1.3)
>
> SSL/TLS > Edge Cerificates > TLS 1.3 (true) 

> [!NOTE]
> С правилами маршрутизации для России.

### Включает:
1) Настройку сервера 3X-UI Xray (протоколы Trojan Tls и VLESS Reality, подписка, json подписка)
2) Настройку обратного прокси NGINX на 443 порту
3) Настройку безопасности, включая автоматические обновления (unattended-upgrades)
4) SSL сертификаты Cloudflare с автоматическим обновлением
5) WARP
6) Включение BBR
7) Настройка UFW
8) Настройка SSH за NGINX
9) Отключение IPv6
10) Шифрование DNS запросов systemd-resolved или adguard-home (DNS over TLS или DNS over HTTPS) 

-----

### Использование:

Для настройки сервера запустите эту команду:

```
bash <(curl -Ls https://github.com/cortez24rus/xui-reverse-proxy/raw/refs/heads/main/xui-rp-install.sh)
```

Затем введите необходимую информацию:

![image](https://github.com/user-attachments/assets/dc60caee-1b01-40c9-a344-e0a67ebfc2ee)

Скрипт покажет необходимые ссылки и данные для входа.
