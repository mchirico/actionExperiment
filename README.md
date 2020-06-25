## Notes

Only the owner of the repo, or a pull request with a 
proper label can run actions.


```
git remote add upstream https://github.com/mchirico/actionExperiment.git

git push -u origin n

git fetch upstream
git merge upstream/master


```

## Sample

```
cat ~/.gitconfig
[user]
    email = monk@sterlingpizza.com
[core]
    editor = emacs

[alias]
    st = status
    co = checkout
    p = push
    fo = fetch upstream
    di = diff --staged
    ll = log --format=%B origin..HEAD
    br = branch
    cm = commit -am 'update'
        rb = rebase master -i
    l =  log --oneline
    ls =  log --stat
    lp = log -p
    ln = log --oneline notes/commits
    la = log --oneline --graph --decorate --all


```





## Build with vendor
```
export GO111MODULE=on
go mod init
# Below will put all packages in a vendor folder
go mod vendor



go test -v -mod=vendor ./...

# Don't forget the "." in "./cmd/script" below
go build -v -mod=vendor ./...
```


## Don't forget golint

```

golint -set_exit_status $(go list ./... | grep -v /vendor/)

```


