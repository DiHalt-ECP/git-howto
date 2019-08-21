# Как удалить файлы, перечисленные в .gitignore, но которые уже проиндексированы git или находятся в репозитории git?

## Answer #1

Вы можете удалить их из репозитория вручную:
```shell
git rm --cached file1 file2 dir/file3
```

Или, если у вас много файлов:
```shell
git rm --cached `git ls-files -i --exclude-from=.gitignore`
```

Но это не работает в Git Bash в Windows. Он выдает сообщение об ошибке. Следующее работает лучше:
```shell
git ls-files -i --exclude-from=.gitignore | xargs git rm --cached  
```


## Answer #2

Более простой способ работы с любой ОС - сделать
```shell
git rm -r --cached .
git add .
git commit -m "Removing all files in .gitignore"
```

В основном вы читаете все файлы, кроме тех, что содержатся в .gitignore

