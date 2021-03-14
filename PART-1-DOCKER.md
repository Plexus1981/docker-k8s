Intro to Docker
===============
8 часов, 2 ак. дня.

Prerequisites
=============
- [ ] RAM ≥ 4Gb
- [ ] [Поддерживаемая ОС с установленным Docker](https://docs.docker.com/engine/install/)
- [ ] Сетевой доступ к [hub.docker.com](https://hub.docker.com)

Agenda
======
Введение в Docker
-----------------
- [ ] Зачем нужен Docker? Функции.
- [ ] Процесс ОС "на стероидах": какие ресурсы необходимо изолировать и инкапсулировать?
- [ ] Метафора морского контейнера
- [ ] Виртуализация или контейнеризация?
- [ ] Как устроен Docker? Элементы.
- контейнеризованное приложение
- docker daemon
- container
- disk image
- disk image provisioning tool and language: Dockerfile
- Docker image registries: [docker hub](http://hub.docker.com) and corporate registries

Hands-on practice quest #00: prerequisites sound-check
---------------------------
- [ ] Given сформированы пары участников
- [ ] When участники используют команды и проанализируют их вывод и поведение
```shell
docker --version
```
```shell
docker run hello-world
```
- [ ] Then участники делятся возникшими и решенными проблемами и отвечают на вопросы
- Успешна ли сконфигурирована система для использования docker?
- Откуда взялся образ диска?
- Какой раз по счету был запущен на данной машине контейнер с образом hello-world?

Жизненный цикл образа
---------------------
- [ ] Изоляция дискового доступа для контейнера
- [ ] Что должно быть на диске для запуска и работы контейнеризованного приложения?
- [ ] Состав образа диска
- [ ] Отображение образа на диск хостовой системы
- [ ] Прием copy-on-write и OverlayFS
- [ ] Жизненный цикл образа и аналогии с git
- [ ] Идентификация образов: имена, версии, теги
- [ ] Semantic versioning vs unique tags
- [ ] Хранение образа на хостовой системе и в репозиториях

Hands-on practice quest #01: disk image lifecycle
---------------------------
- [ ] Given пары участников
- [ ] When участники используют команды и проанализируют их вывод и поведение
```shell
docker images
docker images --all
```
```shell
docker rmi hello-world
docker rmi hello-world --force
docker images
```
```shell
docker search alpine
docker pull adoptopenjdk/openjdk8:alpine-jre
docker images --all
```
- [ ] Then участники делятся возникшими и решенными проблемами и отвечают на вопросы
- Сколько контейнеров было на хосте?
- Сколько места на диске хоста занимает каждый образ?
- Сколько места на диске хоста занимает каждый контейнер?
- Какие приложения былы контейнеризованы?

Жизненный цикл контейнера
-------------------------
- [ ] Просмотр активных контейнеров: работающих и остановленных
- [ ] Именование контейнера
- [ ] Какие ресурсы хоста нужно выделить для запуска контейнера?
- [ ] Запуск контейнера: run vs start
- [ ] Ключевые параметры запуска контейнера
- [ ] Подключение к рабочему контейнеру
- [ ] Остановка контейнера
- [ ] Удаление контейнера и его физический смыл
- [ ] Журнал контейнера

Изоляция данных
---------------
- [ ] Как контейнер работает с данными?
- [ ] Что происходит с изменениями в образе при остановке контейнера?
- [ ] Stateful VS Stateless containers
- [ ] Как зафиксировать изменения в образе?
- [ ] Как откатить изменения в образе?
- [ ] Как можно сохранять изменения на диске вне образа?
- Shared folders
- Volumes
- [ ] Жизненный цикл docker volume

Виртуализация сети
------------------
- [ ] Отображение портов
- [ ] Варианты сетевой топологии между хостом и контейнером
- [ ] Варианты сетевой топологии между контейнерами
- [ ] Разрешение адресов и имен в виртуализированных сетях 

Изоляция хостовых ресурсов
--------------------------
- [ ] Отображение портов
- [ ] Установка переменных окружения ОС для контейнера
- [ ] Лимитирование памяти
- [ ] Лимитирование CPU
- [ ] Особенности настройки контейнеризированных приложений с учетом лимитирования ресурсов

Контейнеризация простого сервиса
--------------------------------
- [ ] Что необходимо сконфигурировать для создания образа диска с простым сервисом?
- [ ] Команды сборки диска и роль Dockerfile
- [ ] Структура Dockerfile и его декларативность
- [ ] Ключевые директивы
- `FROM`
- `ADD` vs `COPY` (+ `.dockerignore`)
- `RUN`
- `ENTRYPOINT` vs `CMD` (+ `shell` vs `exec` formats)
- `ENV`
- `EXPOSE`
- `VOLUME`

Оптимизация сборки образов
--------------------------
- [ ] Директивы Dockerfile как слои образа
- [ ] Как уменьшить размер образа?
- [ ] Как ускорить сборку образа?
- [ ] Кеширование включаемых файлов и результатов директив
- [ ] Составные команды
- [ ] Порядок директив 
- [ ] Выбор образа-предка: легковесные ОС, busybox и `scratch`-образ
- [ ] Паттерн "multi-stage" для сборки и запуска

Введение в контейнеризацию составного приложения
------------------------------------------------
- [ ] Обзор Docker Compose
- [ ] C Dockerfile и без него
- [ ] Структура и пример docker-compose.yml 
- [ ] Ограничения Docker Compose

Рекомендуемые практики
----------------------
- [ ] Запуск от выделенного пользователя
- [ ] Хранение и передача secrets
- [ ] Локальное журналирование и доступ к логам
- docker logging drivers
- shared folders or volumes
- sidecars containers
- remote log collectors
- [ ] Мониторинг
- [ ] "Docker-из-docker"

Docker в среде Kubernetes
-------------------------
- [ ] k8s больше не поддерживает docker: все пропало?
- [ ] Как устроен Docker? Элементы.
- [ ] Какие существуют аналоги?
- [ ] Как устроены аналоги? Элементы.