Status of workflow

![example workflow](https://github.com/Lancelot-knight/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?event=push)

# Проект YAMDB_FINAL

## Автор проекта: Алексей Неклоюдов (https://github.com/Lancelot-knight)

## Описание
Проект для закрепления практических навыков DevOps: CI и CD.

## Технологии
Python 3.7
Django 2.2.19
Docker 20.10.12

## Как развернуть проект:

### Сделать ответвление от данного репозитория(fork), перейти в свой, клонировать репозиторий на локальную машину:
```git clone https://github.com/<ваш_username>/yamdb_final.git```
### В своем репозитории создать и заполнить workflow(Actions -> set up a workflow yourself):
- скопировать файл yamdb_workflow.yml из корня проекта;
- поместить его в папку yamdb_final/.github/workflows/;
- остальные файлы из этой папки удалить.
### В настройках своего репозитория добавьте Secrets GutHub Actions переменные окружения(Settings -> Secrets -> Actions -> New repository secret) по списку:
```
для работы базы данных:
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=
POSTGRES_PASSWORD=
DB_HOST=db
DB_PORT=5432

для подключению к Docker Hub:
DOCKER_USERNAME=
DOCKER_PASSWORD=
DOCKER_IMAGE=<ваш-логин-на-docker-hub/ваш-репозиторий-на-docker-hub:latest>

для подключения к удаленному серверу:
SSH_KEY=<приватный ключ>
USER=
HOST=<ip-адрес вашего сервера>
PASSPHRASE=<если имеется>

для отправки уведомлений в Telegram:
TELEGRAM_TO=<id своего телеграм-аккаунта>
TELEGRAM_TOKEN=<токен вашего телеграм-бота>
``` 
### Заменить Docker image в файле docker-compose.yaml:
в строке 11, блок контейнера web, заменить значение image:
```
web:
    image: <ваш-логин-на-docker-hub/ваш-репозиторий-на-docker-hub:latest>
    restart: always
    volumes:
    ...
```
### Проверьте работоспособность приложения:
1. На локальной машине из папки проекта последовательно выполните команды:
```git add .```
```git commit -m"test push"```
```git push```
2. Посмотрите во вкладке Action своего репозитория ход и результаты выполнения файла workflow.
3. Проверьте получение сообщения в Telegram, в случае успешного выполнения workflow.
4. зайдите на 
http://<ваш-ip-адрес-удаленного-сервера>/admin/ и убедитесь, что страница отображается полностью: статика подгрузилась.
(в данном случае http://51.250.24.187/admin)