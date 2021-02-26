# How to use vim's native package manager

## Setup
```
mkdir -p ~/.config/pack/plugins/start
mkdir -p ~/.config/pack/plugins/opt
```
`plugins` may be anything else and can be used to categorize the plugins. The
`start` subdirectory is loaded on startup and `opt` is loaded manually via
:packadd {name}

## Using git submodules to manage plugins (WIP)

If it's not a git directory, just use `git clone` and `rm`.

### Installing
```
git submodule add repo_url path/to/plugins/dir
git commit -m "Installed plugin X"
```

### Updating
```
git submodule foreach git pull origin master
git add .
git commit -m "update submodules"
```

### Uninstalling
```
git submodule deinit path/to/submodule
git rm path/to/submodule
```
or
```
git rm the_submodule
rm -rf .git/modules/the_submodule
```

## Generating helptags
```
vim -c 'helptags path/to/plugin/doc/folder' -c quit
```

[Reference](https://www.danielfranklin.id.au/vim-8-package-management/)  
[Reference](https://shapeshed.com/vim-packages/#vim-8-brings-native-third-party-package-loading)

#vim
#neovim
#git
