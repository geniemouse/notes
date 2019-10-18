# VLT

_Vault_ (VLT) is AEM's local file > local AEM instance synchronisation system for file changes. The commands are similar to `svn` version control.

<!-- MarkdownTOC -->

1. [Setup VLT](#setup-vlt)
1. [Basic commands](#basic-commands)
    1. [More commands](#more-commands)
    1. [`vltremove` & `vltco` aliases](#vltremove--vltco-aliases)
1. [IDE plugins](#ide-plugins)
    1. [Sublime Text VLT plugin](#sublime-text-vlt-plugin)

<!-- /MarkdownTOC -->

## Setup VLT

**NOTE:** All VLT commands should be from inside the relevant `jcr_root` folder.

1. Navigate to `jcr_root`
2. Checkout files  
   `vlt --credentials admin:admin co --force http://localhost:4502/crx`

## Basic commands

-   Status: `vlt st`
-   Status update with round trip to AEM: `vlt st -u`
-   Check-in/commit: `vlt ci <NAME_OF_FILE>`
-   Get latest/pull: `vlt update`
-   Push local changes: `vlt up`

### More commands

https://gist.github.com/asabaylus/2951791

Reproduced here:

```
# checkout files
vlt --credentials admin:admin co --force http://localhost:4502/crx

# remove from CRX all files deleted from file system
$ vlt st | grep ! | cut -c 2- | xargs -I {} vlt rm {}

# add to CRX all files not yet in vlt control
$ vlt st | grep \? | cut -c 2- | xargs -I {} vlt add {}

# add all missing files into the CRX
vlt st | grep ^A | cut -c 2- | xargs -I {} vlt commit --force {}

# copy all modified files into the CRX
vlt st | grep ^M | cut -c 2- | xargs -I {} vlt commit --force {}

# delete all deleted files from the CRX
vlt st | grep ^D | cut -c 2- | xargs -I {} vlt commit --force {}

# strip .vlt files from all directories below the current directory
find . -name "*.vlt" -exec rm -rf {} \;
```

### `vltremove` & `vltco` aliases

Add these aliases to your Bash profile.

Sometimes the only way to deal with VLT issues is to strip the `.vlt` files and redo the checkout.

```
# Create VLT system variable
export VLT_HOME=/usr/local/bin/vlt

# System aliases
alias vltremove="find . -name .vlt -print0 | xargs -0 rm"
alias vltco="vlt --credentials admin:admin co --force http://localhost:4502/crx"
```

## IDE plugins

### Sublime Text VLT plugin

-   [Package Manager information](https://packagecontrol.io/packages/Vlt)
-   [GitHub repo](https://github.com/tomalec/Sublime-Text-2-Vlt-Plugin)
