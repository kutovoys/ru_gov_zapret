
# Zapret RU GOV
Блокировка доступа к запрещенным в РФ сервисам сайтам

Файл обновляется регулярно и автоматически, подгружая последние списки запрета.

Актуальная версия всегда доступна по адресу 
```bash
wget -O https://github.com/kutovoys/ru_gov_zapret/releases/latest/download/zapret.dat
```

Имеет две ветки:
1) zapret.dat:zapret - Все что заблокировано РКН
1) zapret.dat:zapret-zapad - Ресурсы не обслуживающие Русские IP

## Установка для сервера

Создаем папку 
```bash
mkdir -p /var/lib/marzban/assets/
```
Скачиваем 
```bash
wget -O /var/lib/marzban/assets/zapret.dat https://github.com/kutovoys/ru_gov_zapret/releases/latest/download/zapret.dat
```
Устанавливаем значение в .env файле

```XRAY_ASSETS_PATH = "/var/lib/marzban/assets/"```

Редактируем xray_config.json
```json
    "routing": {
        "domainStrategy": "IPIfNonMatch",
        "rules": [
            {
                "outboundTag": "BLOCK",
                "domain": [
                    "ext:zapret.dat:zapret",
                    "ext:zapret.dat:zapret-zapad"
                ],
                "type": "field"
            }
        ]
    }
```

{{add}}
