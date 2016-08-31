## Setting up

```sh
git config --global user.name "<username>"
git config --global user.email "<email address>"
```
## Uploading

```sh
git add <file/folder>
git commit -m "<message>"
git push -u origin master
```

```sh
git fetch
git checkout
git merge
```

## Branches
```sh
git branch -a
git checkout <branch>
```

## Cache username/password authentication for 1 hour
```sh
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=3600'
```
