# XUI-REVERSE-PROXY

-----

### Прокси с использованием протоколов Trojan и VLESS (Reality) за реверс-прокси NGINX
Этот скрипт предназначен для быстрой и простой настройки скрытого прокси-сервера, использующего протоколы Trojan TLS и VLESS (Reality), с маскировкой через NGINX. В данном варианте все входящие запросы обрабатываются NGINX, а сервер работает как прокси-сервер только при условии, что запрос содержит правильный путь (URI). Это повышает безопасность и помогает скрыть истинное назначение сервера.

> [!IMPORTANT]
> Этот скрипт был протестирован на Debian 12 в среде виртуализации KVM. Для корректной работы вам потребуется собственный домен, который необходимо привязать к Cloudflare. Скрипт рекомендуется запускать с правами root на свежеустановленной системе.

### Настройка cloudflare
1. Обновите систему и перезагрузите сервер.
2. Настройте Cloudflare:
   - Привяжите ваш домен к Cloudflare.
   - Добавьте следующие DNS записи:

| Type  | Name             | Content          | Proxy status  |
| ----- | ---------------- | ---------------- | ------------- |
| A     | your_domain_name | your_server_ip   | Proxied       |
| CNAME | www              | your_domain_name | DNS only      |
   
3. Настройки SSL/TLS в Cloudflare:
   - Перейдите в раздел SSL/TLS > Overview и выберите Full для параметра Configure.
   - Установите Minimum TLS Version на TLS 1.3.
   - Включите TLS 1.3 (true) в разделе Edge Certificates.

> [!NOTE]
> Скрипт настроен с учётом специфики маршрутизации для пользователей из России.

### Включает в себя:
  
1. Настройку сервера 3X-UI Xray:
   - Протоколы Trojan TLS и VLESS Reality.
   - Подключение подписки и JSON подписки для автоматического обновления конфигураций.
2. Настройку обратного прокси на NGINX на порту 443.
3. Обеспечение безопасности:
   - Автоматические обновления системы через unattended-upgrades.
4. Настройка SSL сертификатов Cloudflare с автоматическим обновлением для защиты соединений.
5. Настройка WARP для защиты трафика.
6. Включение BBR — улучшение производительности TCP-соединений.
7. Настройка UFW (Uncomplicated Firewall) для управления доступом.
8. Настройка SSH за NGINX, скрывая реальный SSH-порт.
9. Отключение IPv6 для предотвращения возможных уязвимостей.
10. Шифрование DNS-запросов с использованием systemd-resolved или AdGuard Home (DNS over TLS или DNS over HTTPS).

-----

### Использование:

Для настройки сервера выполните следующую команду:

```
bash <(curl -Ls https://github.com/cortez24rus/xui-reverse-proxy/raw/refs/heads/main/xui-rp-install.sh)
```

Затем введите необходимую информацию:

![image](https://github.com/user-attachments/assets/dc60caee-1b01-40c9-a344-e0a67ebfc2ee)

[!IMPORTANT] Скрипт предоставит все необходимые ссылки и данные для входа в административную панель XUI, а также другие важные данные для дальнейшей работы.
