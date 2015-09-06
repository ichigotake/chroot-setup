# NAME

chroot-setup - [WIP] Set up utility for chroot(2)

## SYNOPSYS

```sh
$ chroot-setup [sub_command] [directory] [args...]
```

## SUPPORT ENVIRONMENT

- Mac OS X 10.10.4 / bash
- OpenBSD 5.7 / ksh

## INSTALLATION

### Basic GitHub Checkout

1. Check out chroot-setup into `~/.chroot-setup`

    $ git clone git://github.com/ichigotake/chroot-setup.git ~/.chroot-setup

2. Add ~/.chroot-setup/bin to your $PATH for access to the chroot-setup command-line utility.

    ~~~ sh
    $ echo 'export PATH="$HOME/.chroot-setup/bin:$PATH"' >> ~/.bash_profile
    ~~~
    
    **Ubuntu note: Modify your ~/.profile instead of ~/.bash_profile.**
    
    **Zsh note: Modify your ~/.zshrc file instead of ~/.bash_profile.**

3. Restart your shell as a login shell so the path changes take effect.
    You can now begin using chroot-setup.

    ~~~ sh
    $ exec $SHELL -l
    ~~~

#### Upgrading

If you've installed chroot-setup manually using git, you can upgrade your
installation to the cutting-edge version at any time.

~~~ sh
$ cd ~/.chroot-setup
$ git pull
~~~

To use a specific release of chroot-setup, check out the corresponding tag:

~~~ sh
$ cd ~/.chroot-setup
$ git fetch
$ git checkout 2.0.0
~~~

## Command Reference

Like `git`, the `chroot-setup` command delegates to subcommands based on its
first argument. The most common subcommands are:

### chroot-setup cp

```sh
$ chroot-setup add /path/to/my-container /usr/bin/env
$ ls -l /path/to/my-container/usr/bin/env
-rw-r--r--  1 ichigotake  staff  14224  8 31 13:49 /path/to/my-container/usr/bin/env
```

### chroot-setup deps


### chroot-setup init

```sh
$ chroot-setup init /path/to/my-container
Created!: /path/to/my-container

$ tree my-container
├── bin
│   └── bash
├── dev
|   ...
│   └── zero
└── usr
    └── lib
    ...
        ├── libDiagnosticMessagesClient.dylib
        └── system
            ├── libcache.dylib
            ...
            └── libxpc.dylib
```

## AUTHOR

ichigotake <ichigotake.san@ GMAIL COM>

## LICENSE

Copyright (C) ichigotake

This library is free software; you can redistribute it and/or modify it under the same terms as Perl itself.
