Для упрощения процесса установки вы можете развернуть контейнер (похож на виртуальную машину) со всеми предустановленными зависимостями.

_tl;dr [dockerhub url](https://hub.docker.com/r/justheuristic/nlp_course/)_

## Что такое Docker?

Docker - это платформа для разработки, доставки и запуска приложений в контейнерах. Контейнеры позволяют упаковать приложение со всеми его зависимостями в стандартизированную единицу для разработки программного обеспечения. Это обеспечивает, что приложение будет работать в любой среде, будь то локальный компьютер, частный или общедоступный облак. Таким образом, Docker упрощает развертывание и масштабирование приложений, обеспечивая их изоляцию и безопасность.

## Установка Docker

Мы рекомендуем использовать либо нативный docker (рекомендуется для Linux), либо kitematic (рекомендуется для Windows).
* Установка [kitematic](https://kitematic.com/), простой интерфейс для docker (все платформы)
* Чистый docker: руководство для [windows](https://docs.docker.com/docker-for-windows/), [linux](https://docs.docker.com/engine/installation/), или [macOS](https://docs.docker.com/docker-for-mac/).

Ниже приведены инструкции для обоих подходов.

## Kitematic
Найдите justheuristic/nlp_course в меню поиска. Скачайте и запустите контейнер.

Нажмите на экран "предварительного просмотра веб-страницы" в правом верхнем углу __или__ перейдите в настройки, порты и найдите на каком порту расположен ваш jupyter, обычно это 32***.

## Нативный метод
`docker run -it -v <local_dir>:/notebooks -p <local_port>:8888 justheuristic/nlp_course sh ../run_jupyter.sh`

Например,
`docker run -it -v /Users/mittov/Documents/shad/semester4/ -p 8888:8888 justheuristic/nlp_course sh ../run_jupyter.sh`

После этого вы сможете получить доступ к вашему jupyter в браузере по адресу `localhost:<local_port>`.

Если от вас потребуется ввести токен, вы найдете его в логах контейнера, например, `localhost:8888/?token=ad1a5a0aab43efb47a9a805388fcf508d0b5f84a16e4542b&token=ad1a5a0aab43efb47a9a805388fcf508d0b5f84a16e4542b`.

## Вручную
Сборка контейнера

`$ docker build -t nlp .`

Запуск

`$ docker run --rm -it -v <local_dir>:/notebooks -p <local_port>:8888 nlp`

Примеры:

`$ docker run --rm -it -v /Users/mittov/Documents/shad/semester4/:/notebooks -p 8888:8888 nlp`

Скопируйте токен из консоли и откройте
http://localhost:8888/ (если спрашивают токен, смотрите "нативный метод")

Author: @SoldatParfait