---
title: "Шпаргалка по Hugo"
subtitle: "Установка, настройка, работа с Hugo"
date: 2023-04-01T12:20:28Z
lastmod: 2023-04-01T12:20:28Z
draft: true
authors: []
description: ""

tags: [Hugo, Web, CMS]
categories: [Hugo, Web, CMS]
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: "https://d33wubrfki0l68.cloudfront.net/c38c7334cc3f23585738e40334284fddcaf03d5e/2e17c/images/hugo-logo-wide.svg"
featuredImagePreview: "https://d33wubrfki0l68.cloudfront.net/c38c7334cc3f23585738e40334284fddcaf03d5e/2e17c/images/hugo-logo-wide.svg"

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---
## Установка HUGO
`Hugo` существует в двух версиях обычный и расширенный `hugo_extended`  
Скачать свежую версию можно тут:  
[https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases "https://github.com/gohugoio/hugo/releases")  
Можно установить и из репозитория установленного дистрибутива Linux, но там может быть старая версия:  
`sudo apt install hugo`  
`hugo version` - проверяем версию.

## Быстрый старт
`hugo new site <site_name>`  
`cd <site_name>`  
`git init`  
`git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke`  
`echo "theme = 'ananke'" >> config.toml`  
`hugo server`

## Создание и настройка сайта
`hugo new site <site_name>`  
(создаем новый сайт в текущей директории)  
`cd <site_name>`  
(Переходим в папку с сайтом, иначе команды hugo не будут работать, если выполнять их не из папки с сайтом)  
`git init`  
(Создаём Git-репозиторий в текущей папке)  
Выбираем тему для сайта - [https://themes.gohugo.io/](https://themes.gohugo.io/ "https://themes.gohugo.io/")  
`git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke`  
(Добавляем тему как субмодуль нашего Git-репозитория)  
Темы хранятся в папке `/<site_name>/themes/<themes_name>`  
Редактируем основной файл настроек `config.toml`  
Меняем параметр `theme = '<theme>'` на нашу скаченную тему, например `theme = 'ananke'`

> Так же в этот файл `config.toml` нужно скопировать базоыве настройки рекомендуемые создателями темы, если необходимо.

## Написание постов
`hugo new posts/my-first-post.md`

> По умолчанию все сообщения и страницы создаются как черновики. Если вы хотите отобразить эти страницы, удалите свойство `draft: true` из метаданных, установите свойство `draft: false` или добавьте параметр `-D или --buildDrafts` в команду `hugo`. Метаданные по умолчанию устанавливаются в `/<site_name>/archetypes/default.md`

## Запуск встроенного web-сервера
`hugo server --buildDrafts`  
`hugo server -D`  
`hugo server -D --bind 192.168.1.152`  
`hugo server -D --bind 10.10.10.10 --baseURL http://10.10.10.10/`  
`hugo serve --disableFastRender`

## Генерация статических страниц
`hugo`

> Команда `hugo` создает ваш сайт, публикуя файлы в публичном каталоге `<site_name>/public`. Чтобы опубликовать сайт в другой каталог, используйте флаг `--destination` или установите `publishDir` в конфигурации сайта.

`hugo -D`

## Выгрузка во внешний Git-репозиторий
`git init`  
(Если не делали ранее, создаём Git-репозиторий в текущей папке)  
`git add .`  
`git commit -m "Initial commit"`  
`git remote add origin https://github.com/solox13/it-notes.git`  
`git branch -M main`  
`git push -u origin main`

## Базовый NGINX config для сгенерированного командой hugo статического сайта

```
server {
       listen 80;
       listen [::]:80;

       server_name mysite.com www.mysite.com;

       root /home/username/mysite/public/; #Absolute path to where your hugo site is
       index index.html; # Hugo generates HTML

       location / {
               try_files $uri $uri/ =404;
       }
}
```
