---
title: "Шпаргалка по Docker"
subtitle: "Установка, управление, команды  Docker"
date: 2023-04-01T12:20:28Z
lastmod: 2023-04-01T12:20:28Z
draft: true
authors: []
description: ""

tags: [Docker, Containers]
categories: [Docker, Containers]
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: "https://thingsolver.com/wp-content/uploads/docker-cover.png"
featuredImagePreview: "https://thingsolver.com/wp-content/uploads/docker-cover.png"

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

## Управление контейнерами (container)
`docker ps` - список запущенных контейнеров.
`docker ps -a` - список всех созданных контейнеров, запущенных и остановленных.  
`docker rm <container id or name>` - удалить контейнер.  
`docker start | stop | pause | unpause | kill <container id or name>` - запуск | остановка | приостановка | снятие с приостановки | уничтожение контейнера.

## Информация о контейнерах (container)
`docker inspect <container id or name>` - вся информация о контейнере.  
`docker stats <container id or name>` - информация о потреблении ресурсов контейнером.  
`docker logs <container id or name>` - просмотр логов внутри контейнера.  
`docker logs -f <container id or name>` - просмотр лайв логов внутри контейнера.  

## Вход в контейнер, исполнение команд (container)
`docker exec -it <container id or name> bash <command>` - вход в bash внутри контейнера.  
`docker exec -it <container id or name> /bin/bash <command>` - тоже вход в bash внутри контейнера.  
