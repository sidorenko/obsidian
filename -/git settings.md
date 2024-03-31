#git 
```table-of-contents
```
## Перезапись последних двуx коммитов
``` shell
git reset --soft HEAD~2  
git commit
```

## Aliases
[https://githowto.com/ru/aliases](https://githowto.com/ru/aliases)
``` shell
git config --global alias.ch checkout
git config --global alias.co commit
git config --global alias.ad add
git config --global alias.st status
git config --global alias.lo log
git config --global alias.br branch
git config --global alias.pu pull  
git config --global alias.sh stash


// list
git config --get-regexp alias
```

## Amend with changing commit message
``` shell
git co --amend
```


``` shell
// in vim after changing commit message

:w
:q!
```

## Force Git to overwrite local files on pull
``` shell
 git reset --hard origin/master  
 git fetch origin master  
 git reset --hard origin/master
```

## Branch from a previous commit using git
``` shell
 git checkout -b dev HEAD~1
```
![[Pasted image 20230731113734.png]]

## How to modify existing, unpushed commits?
![[Pasted image 20230731113854.png]]

## Some everyday steps
``` shell
// локальный коммит удалить из индекса (не удаляя изменения)
// (если не надо пока коммитить и нужно спрятать)
git reset --soft HEAD~1

// очистить стек спрятанных изменений
git stash clear

// спрятать локальные изменения
git stash

---

// изменить конкретный коммит на сервере
git st
git ad .
git co --amend --no-edit
git push origin HEAD:refs/changes/158301

---

// отправить изменения на сервер в мастер ветку
git st
git ad .
git co -m "commit"
git push origin HEAD:refs/for/master
```

## How to recover a dropped stash in Git?
``` shell
git fsck --unreachable | grep commit | cut -d" " -f3 | xargs git log --merges --no-walk --grep=WIP

git show <sha1>

git cherry-pick -m 1 <sha1>

--------------------------------------------------------------------------

  // отменить изменения ( to discard changes in working directory )
  git fsck --unreac    // востанавливать, возвращать в исходное положение

  // или 

  git checkout .       // контроль, проверка

--------------------------------------------------------------------------
```

## How do I revert all local changes in Git managed project to previous state?
```shell
// отменить изменения ( to discard changes in working directory )

git reset --hard     // востанавливать, возвращать в исходное положение

// или 

git checkout .       // контроль, проверка
```

## Delete a branch (local or remote)
```shell
git branch -D
```