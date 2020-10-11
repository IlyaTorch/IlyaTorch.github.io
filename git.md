Загрузить гит можно тут: http://git-scm.com/downloads
```git
$ gitk
$ git-gui
```
# Генерация пары ssh ключей:

     ssh-keygen -t rsa –C “vitali_shulha@epam.com"

Публичный ключ (id_rsa) нужно отправить владельцу репозитория для получения прав работы. Или загрузить в настройки профиля в bitbucket/github/gitlab

# Настройка имени пользователя и емейла:

     git config --global user.name “Ilya Torch“

     git config --global user.email “torch.ilya@gmail.com"

# Откат изменений
![image](https://sun9-74.userapi.com/xu99LVU67T3FrB_isys4kU0Z8nD9PTaxtJ4m6A/6ALmxoaetus.jpg)

# Удаление коммитов (локально) (`git reset`)
![image](https://sun9-42.userapi.com/qa5DThqIm5ketQZP0KIPhnWbwTHlBELkqCjCUQ/rRWzWUH00i8.jpg)

# Удаление коммитов (из удаленного реппозитория) (`git revert`)

![image](https://sun9-9.userapi.com/a1XTkZj3ZrrwvQGDhhGKGzVO2Ft38YZfYxMOww/K9cjV3AUxq0.jpg)

# Ветки
**Переключение на другую ветку**:
`git checkout feature`

# Мерж
**Cписок веток в репозитории**: `git branch --all`
**Создание новой ветки и переключение на нее**: `git checkout -b branch-name`

Чтобы смержить ветки, нужно перейти в тот бранч, в который хочу влить изменения. И далее: `git merge another-branch`
**Перейти на ветку**: `git checkout branch-name`
## Виды мержей
* fast-forward merge — (перемотка) перестановка указателя (C в master ветке на F)
![img](https://sun9-41.userapi.com/HAPKQjcNrkAvt1mIkzDTnReKD-YD3aGJT_KBqw/GyKvWQ12wCM.jpg)
---
* non-fast-forward merge — создается доп коммит

![img](https://sun9-52.userapi.com/ZUBEG5c0-SKC56XXgF_PHbn-hi29mI1KVCl0-A/tG5D1-aVhMo.jpg)
![img](https://sun9-40.userapi.com/2UXZa6HTvnOPouMEnzYHe23Z7FOo2RyfuagnyQ/3tzFXfprKsA.jpg)
# Решение конфликтов при мердже
![image](https://sun9-53.userapi.com/oqgd3EJO720kBiclEz4Kd_-MDuZAW-LNsLhsxg/I7XqnTwlB4E.jpg)
Также **конфликт при слиянии веток** можно решить следующим образом:
 * исправить содержимое файлов с конфликтами
 * сделать коммит изменений

ИЛИ: `git merge --continue`
# Git rebase
Перенос указателя со старого коммита на более новый(при работе с ветками). Т.е. используется для синхронизайии своих веток с `upstream`. Вместо мержа

![img](https://sun9-38.userapi.com/s2Hd0GK5Fl2-aSZ_h59OBX20kJou2pdoKdtKeg/8GJziciFkwM.jpg)
![img2](https://sun9-43.userapi.com/caBRj3kAQlHl0Z1MznILehvbo5TFlniI0acrLA/r9pCumHBOl4.jpg)

# `Cherry-pick`
**`cherry-pick`** — копирование коммита в другое место

# Tags
**Tag** — текстовый маркер, которым можно пометить коммит.
Можно отдельно запушить теги.

![img](https://sun9-26.userapi.com/-ARUwKpkc1DeItn-z3ywWwtszMzyPOIAyiJ5mw/1ICeb5ycZkg.jpg)
1. Пометить тегом коммит
2. Список тегов
3. Запушить все теги
4. Переключиться на коммит по тегу

# Stashing
**Stash** позволяет сохранить незакомиченную работу в некоторое хранилище. Применяется только к отслеживаемым (`git add `) файлам.
**Добавить в stash**:
`git stash save "stash-description"`
**Взять из stash'a**:
`git stash apply stash-id` или `git stash pop stash-id`
![img](https://sun9-29.userapi.com/hnrYFk0qcSdVaFVsEzeumjUKibbXbExxcQ3xyw/OanOhD38KH4.jpg)
`git stash pop stash-id` — применяет stash и удаляет его
`git stash apply stash-id` — применяет stash и оставляет его в спеске stash list
`git stash drop stash-id` — удалить ненужный stash

# Remotes
![img](https://sun9-24.userapi.com/Yo0ukYnj0VZpVPDA1HigRVAVkzfrLH_5cUcDBg/JwFZW7ZJXiw.jpg)
**Удалить удаленный репозиторий**: `git remote remove origin`

# Дополнительные команды
![img](https://sun9-21.userapi.com/iQHanDrIg_8Wtlg1pHzLab40vZRvRXZ79_tlNA/8M5kldG6918.jpg)
* `git config --global core.editor "'D:\programs\Sublime Text 3\sublime_text.exe'"` — настроить свой редактор для работы с гитом(вместо вима)
* `git blame filename` — кто редактировал файл
* `git bisect ` — бинарный поиск
* `git log ...` — кастомизация
* `git log master..feature` — разница между бранчами `master` и `feature`. 
* `git filter-branch --tree-filter 'rm -f passwords.txt' Head` — проходит по ветке и применяет скрипт(тут удаляет из всех коммитов файл passwords.txt)[сначала лучше проверить эту команду на копии репозитория]
* `git rerere` — патерны решения конфликтов
* `git submodule` — вложенный гит реппозиторий

# Изменение даты коммитов
```
git filter-branch --env-filter \
    'if [ $GIT_COMMIT = bc72b26228f786424053db275c92ed4e32f1f331 ]
     then
         export GIT_AUTHOR_DATE="Sun Oct 4 21:57:14 2020 +0300"
         export GIT_COMMITTER_DATE="Sun Oct 4 21:57:14 2020 +0300"
     fi'
```

**force**:
```git filter-branch -f --env-filter \
    'if [ $GIT_COMMIT = bc72b26228f786424053db275c92ed4e32f1f331 ]
     then
         export GIT_AUTHOR_DATE="Sun Oct 4 21:57:14 2020 +0300"
         export GIT_COMMITTER_DATE="Sun Oct 4 21:57:14 2020 +0300"
     fi'
```

