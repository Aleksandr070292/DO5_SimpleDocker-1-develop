##  Готовый докер

- Возьми официальный докер-образ с nginx и выкачай его при помощи docker pull
![version](screen/1.0.png)

- Проверь наличие докер-образа через docker images
![version](screen/1.1.png)

- Запусти докер-образ через docker run -d [image_id|repository]
![version](screen/1.2.png)

- Проверь, что образ запустился через docker ps
![version](screen/1.2.png)

- Посмотри информацию о контейнере через docker inspect [container_id|container_name] По выводу команды определи и помести в отчёт размер контейнера, список замапленных портов и ip контейнера
![version](screen/1.3.png)
![version](screen/1.4.png)
![version](screen/1.5.png)

- Останови докер образ через docker stop [container_id|container_name] Проверь, что образ остановился через docker ps.
![version](screen/1.6.png)

- Запусти докер с портами 80 и 443 в контейнере, замапленными на такие же порты на локальной машине, через команду run
![version](screen/1.7.png)

- Проверь, что в браузере по адресу localhost:80 доступна стартовая страница nginx
Использовал команду links чтобы открыть в терминале
![version](screen/1.8.png)
![version](screen/1.9.png)

- Перезапусти докер контейнер через docker restart [container_id|container_name].
Проверь любым способом, что контейнер запустился.
![version](screen/1.10.png)

## Операции с контейнером

- Прочитай конфигурационный файл nginx.conf внутри докер контейнера через команду exec
![version](screen/2.0.png)

- Создай на локальной машине файл nginx.conf
- Настрой в нем по пути /status отдачу страницы статуса сервера nginx
![version](screen/2.1.png)


- Скопируй созданный файл nginx.conf внутрь докер-образа через команду docker cp
![version](screen/2.2.png)

- Перезапусти nginx внутри докер-образа через команду exec
![version](screen/2.3.png)

- Проверь, что по адресу localhost:80/status отдается страничка со статусом сервера nginx
![version](screen/2.4.png)

- Экспортируй контейнер в файл container.tar через команду export
![version](screen/2.5.png)

- Останови контейнер
![version](screen/2.6.png)

- Удали образ через docker rmi [image_id|repository], не удаляя перед этим контейнеры.
Удали остановленный контейнер.
![version](screen/2.7.png)

- Импортируй контейнер обратно через команду import
![version](screen/2.8.png)


- Запусти импортированный контейнер
![version](screen/2.9.png)

- Проверь, что по адресу localhost:80/status отдается страничка со статусом сервера nginx
![version](screen/2.4.png)