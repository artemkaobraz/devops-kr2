# КР № 2: вариант 20

Flask-счётчик Образумова Артема Александровича (ЭФБО-02-24) хранит данные в Redis.
Ресурс опубликован через Nginx по адресу `https://kv.devops.local/`.

Приложение и Redis описаны в `docker-compose.yml`. На сервере проект находится
в `~/kr2`, а секрет `REDIS_PASSWORD` хранится только в `~/kr2/.env` с правами 600.
Имена переменных указаны в `.env.example`; сам файл `.env` не доставляется через
rsync и не включается в Git или контекст сборки Docker.

После создания `.env` на сервере запустите `docker compose up -d --build` в
`~/kr2`. Файл `nginx/kr2.conf` устанавливается отдельно в
`/etc/nginx/sites-available/kr2` и активируется ссылкой в `sites-enabled`.
Сертификат `/etc/ssl/certs/kr2.crt` и ключ `/etc/ssl/private/kr2.key`
создаются на сервере для имени `kv.devops.local`; ключу нужны владелец root
и права 600. Применяйте Nginx после `sudo nginx -t` командой
`sudo systemctl reload nginx`.
