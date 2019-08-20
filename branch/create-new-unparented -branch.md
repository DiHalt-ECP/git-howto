## Как создать новую пустую ветку для нового проекта
### Это маленькое руководство о том как создать пустую ветку в Git.
###### Create new unparented branch
---

Если хотите создать новую (см. без родительского коммита) ветку в Git — вам необходимо выполнить следующую команду:
```shell
git checkout --orphan <NEW_BRANCH>
```
Правда при этом все файлы из рабочей директории будут на месте.

Если вы хотите создать новую пустую ветку — вам нужно скомбинировать 2 команды:
```shell
git checkout --orphan <NEW_BRANCH>
git rm -rf .                          # git reset --hard
```
or
```shell
git checkout --orphan <branchname>
git rm --cached -r .
```

Так же параметр --orphan дает возможность создать новую ветку с определенного коммита:
```shell
git checkout --orphan <NEW_BRANCH> <TARGET_REFERENCE>
```
При этом будет создана новая ветка без родительского коммита и в индексе Git будут находится все файлы из выбраного целевого коммита. Подброней можно почитать в [официальной документации Git][1]


[1]: https://git-scm.com/docs/git-checkout        "git-checkout documentation"
