---
title: Git
date: 2020-11-25 18:28:43
background: bg-[#d7593e]
tags:
  - github
  - gitlab
  - version
  - VCS
categories:
  - Linux Command
intro: Этот шпаргалка кратко описывает часто используемые команды Git для быстрой справки.
plugins:
  - copyCode
---

## Начало работы

### Создание репозитория

Создать новый локальный репозиторий

```shell script
$ git init [имя проекта]
```

Клонировать репозиторий

```shell script
$ git clone git_url
```

Клонировать репозиторий в указанную директорию

```shell script
$ git clone git_url моя_папка
```

### Внесение изменений {.row-span-2}

Показать изменённые файлы в рабочем каталоге, подготовленные для следующего коммита

```shell script
$ git status
```

Добавить файл в индекс (staging)

```shell script
$ git add [файл]
```

Добавить все изменённые файлы в индекс

```shell script
$ git add .
```

Зафиксировать все подготовленные файлы в истории версий

```shell script
$ git commit -m "сообщение коммита"
```

Зафиксировать все отслеживаемые файлы в истории версий

```shell script
$ git commit -am "сообщение коммита"
```

Отменить изменения в рабочем каталоге, не подготовленные к коммиту

```shell script
$ git restore [файл]
```

Убрать файл из индекса

```shell script
$ git restore --staged [файл]
```

Убрать файл из индекса, сохранив изменения

```shell script
$ git reset [файл]
```

Откатить всё к последнему коммиту

```shell script
$ git reset --hard
```

Показать разницу между изменениями и индексом

```shell script
$ git diff
```

Показать разницу между индексом и последним коммитом

```shell script
$ git diff --staged
```

Применить коммиты текущей ветки поверх указанной

```shell script
$ git rebase [ветка]
```

### Конфигурация

Задать имя, которое будет прикреплено к вашим коммитам и тегам

```shell script
$ git config --global user.name "имя"
```

Задать email, который будет прикреплён к вашим коммитам и тегам

```shell script
$ git config --global user.email "email"
```

Включить цветной вывод Git

```shell script
$ git config --global color.ui auto
```

Открыть глобальный конфигурационный файл в редакторе

```shell script
$ git config --global --edit
```

### Работа с ветками

Показать все локальные ветки

```shell script
$ git branch
```

Показать все ветки, локальные и удалённые

```shell script
$ git branch -av
```

Переключиться на `my_branch` и обновить рабочий каталог

```shell script
$ git checkout my_branch
```

Создать новую ветку `new_branch`

```shell script
$ git checkout -b new_branch
```

Удалить ветку `my_branch`

```shell script
$ git branch -d my_branch
```

Слить ветку `branchA` в `branchB`

```shell script
$ git checkout branchB
$ git merge branchA
```

Добавить тег к текущему коммиту

```shell script
$ git tag my_tag
```

### Просмотр репозитория

Показать историю коммитов для активной ветки

```shell script
$ git log
```

Показать коммиты в `branchA`, которых нет в `branchB`

```shell script
$ git log branchB..branchA
```

Показать коммиты, изменившие файл (даже после переименования)

```shell script
$ git log --follow [файл]
```

Показать разницу между ветками

```shell script
$ git diff branchB...branchA
```

Показать любой объект Git в читаемом виде

```shell script
$ git show [SHA]
```

### Синхронизация

Загрузить все ветки с удалённого репозитория

```shell script
$ git fetch [псевдоним]
```

Слить удалённую ветку с текущей

```shell script
$ git merge [псевдоним]/[ветка]
# Без fast-forward
$ git merge --no-ff [псевдоним]/[ветка]
# Только fast-forward
$ git merge --ff-only [псевдоним]/[ветка]
```

Отправить локальные коммиты на удалённый репозиторий

```shell script
$ git push [псевдоним] [ветка]
```

Загрузить и слить изменения с отслеживаемой ветки

```shell script
$ git pull
```

Слить конкретный коммит из другой ветки

```shell script
$ git cherry-pick [id_коммита]
```

### Удалённый репозиторий

Добавить URL репозитория как псевдоним

```shell script
$ git remote add [псевдоним] [url]
```

Показать имена настроенных удалённых репозиториев

```shell script
$ git remote
```

Показать имена и URL удалённых репозиториев

```shell script
$ git remote -v
```

Удалить удалённый репозиторий

```shell script
$ git remote rm [имя]
```

Изменить URL удалённого репозитория

```shell script
$ git remote set-url origin [git_url]
```

### Временные коммиты

Сохранить текущие изменения и подготовленные файлы

```shell script
$ git stash
```

Показать список сохранённых изменений

```shell script
$ git stash list
```

Применить верхний stash

```shell script
$ git stash pop
```

Удалить верхний stash

```shell script
$ git stash drop
```

### Отслеживание изменений путей

Удалить файл из проекта и подготовить удаление к коммиту

```shell script
$ git rm [файл]
```

Переместить файл и подготовить перемещение

```shell script
$ git mv [старый_путь] [новый_путь]
```

Показать логи коммитов с информацией о перемещённых файлах

```shell script
$ git log --stat -M
```

### Игнорирование файлов

```
/logs/*

# "!" значит не игнорировать
!logs/.gitkeep

/# Игнорировать системные файлы Mac
.DS_store

# Игнорировать папку node_modules
node_modules

# Игнорировать конфигурацию SASS
.sass-cache
```

Файл `.gitignore` указывает файлы и папки, которые Git должен игнорировать

## Полезные приёмы

### Переименование ветки

- #### **Переименовать** в `new_name`

  ```shell script
  $ git branch -m <new_name>
  ```

- #### **Запушить** и сбросить

  ```shell script
  $ git push origin -u <new_name>
  ```

- #### **Удалить** старую ветку на удалённом репозитории

  ```shell script
  $ git push origin --delete <old>
  ```

  {.marker-timeline}

### Логи

Найти изменения по содержимому

```shell script
$ git log -S'<слово_в_коде>'
```

Показать изменения конкретного файла со временем

```shell script
$ git log -p <имя_файла>
```

Красивое визуальное отображение лога

```shell script {.wrap}
$ git log --pretty=oneline --graph --decorate --all
```

### Ветки {.row-span-2}

Показать все ветки и их upstream

```shell script
$ git branch -vv
```

Быстро переключиться на предыдущую ветку

```shell script
$ git checkout -
```

Показать только удалённые ветки

```shell script
$ git branch -r
```

Взять один файл из другой ветки

```shell script
$ git checkout <ветка> -- <файл>
```

### Переписывание истории

Переписать сообщение последнего коммита

```shell script
$ git commit --amend -m "новое сообщение"
```

Изменить последний коммит без изменения сообщения

```shell script
$ git commit --amend --no-edit
```

См. также: [Rewriting history](https://www.atlassian.com/git/tutorials/rewriting-history)

### Алиасы Git

```cmd
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

См. также: [More Aliases](https://gist.github.com/johnpolacek/69604a1f6861129ef088)

## Продвинутый Git

### Подмодули

Создать новый подмодуль в репозитории:

```shell script
$ git submodule add <url_репозитория> <путь>
```

Клонировать репозиторий и инициализировать его подмодули:

```shell script
$ git clone --recursive <url_репозитория>
```

Обновить все подмодули до последних коммитов:

```shell script
$ git submodule update
```

Загрузить последние изменения подмодулей:

```shell script
$ git submodule update --remote
```

Удалить подмодуль из репозитория:

```shell script
$ git submodule deinit <путь>
$ git rm <путь>
$ git commit -m "Удалён подмодуль"
```

### Cherry-pick

Cherry-pick позволяет применить конкретный коммит из одной ветки в другую.

```shell script
$ git cherry-pick <хеш_коммита>
```

### Reflog

Показать историю изменений HEAD и веток:

```shell script
$ git reflog
```

Найти хеш потерянного коммита или ветки и вернуть его:

```shell script
$ git checkout <хеш_коммита_или_ветки>
```
