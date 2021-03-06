# NAME

chroot-setup - Set up utility with chroot(8)

## SYNOPSIS

```sh
## chroot-setup [sub_command] [directory] [args...]

% chroot-setup init /path/to/my-container
% chroot-setup add /path/to/my-container `whereis ls` `whereis env`
% chroot my-container
[my-container]% env ls
```

## STATUS

**Changes API without notice because develop for me.**

If interesting to this, feedoback to [issues](https://github.com/ichigotake/chroot-setup/issues) or [@ichigotake](https://twitter.com/ichigotake).

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
    
    **OpenBSD note: Modify your ~/.profile instead of ~/.bash_profile.**
    
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

## Command Reference

Like `git`, the `chroot-setup` command delegates to subcommands based on its
first argument. The most common subcommands are:

### chroot-setup add

```sh
$ chroot-setup add /path/to/my-container /usr/bin/env
$ ls -l /path/to/my-container/usr/bin/env
-rw-r--r--  1 ichigotake  staff  14224  8 31 13:49 /path/to/my-container/usr/bin/env
```

### chroot-setup deps

List dynamic object dependencies(with `ldd` or `otool`).

```sh
$ chroot-setup deps `whereis bash`
/bin/bash
/usr/lib/libDiagnosticMessagesClient.dylib
/usr/lib/libSystem.B.dylib
/usr/lib/libauto.dylib
/usr/lib/libc++.1.dylib
/usr/lib/libc++abi.dylib
/usr/lib/libncurses.5.4.dylib
/usr/lib/libobjc.A.dylib
/usr/lib/system/libcache.dylib
/usr/lib/system/libcommonCrypto.dylib
/usr/lib/system/libcompiler_rt.dylib
/usr/lib/system/libcopyfile.dylib
/usr/lib/system/libcorecrypto.dylib
/usr/lib/system/libdispatch.dylib
/usr/lib/system/libdyld.dylib
/usr/lib/system/libkeymgr.dylib
/usr/lib/system/liblaunch.dylib
/usr/lib/system/libmacho.dylib
/usr/lib/system/libquarantine.dylib
/usr/lib/system/libremovefile.dylib
/usr/lib/system/libsystem_asl.dylib
/usr/lib/system/libsystem_blocks.dylib
/usr/lib/system/libsystem_c.dylib
/usr/lib/system/libsystem_configuration.dylib
/usr/lib/system/libsystem_coreservices.dylib
/usr/lib/system/libsystem_coretls.dylib
/usr/lib/system/libsystem_dnssd.dylib
/usr/lib/system/libsystem_info.dylib
/usr/lib/system/libsystem_kernel.dylib
/usr/lib/system/libsystem_m.dylib
/usr/lib/system/libsystem_malloc.dylib
/usr/lib/system/libsystem_network.dylib
/usr/lib/system/libsystem_networkextension.dylib
/usr/lib/system/libsystem_notify.dylib
/usr/lib/system/libsystem_platform.dylib
/usr/lib/system/libsystem_pthread.dylib
/usr/lib/system/libsystem_sandbox.dylib
/usr/lib/system/libsystem_secinit.dylib
```

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

### chroot-setup itself

Copyright (C) ichigotake

This library is free software; you can redistribute it and/or modify it under the same terms as Perl itself.

### plenv

Most of part was inspired from [plenv](https://github.com/tokuhirom/plenv).

```
Copyright (C) Tokuhiro Matsuno

This library is free software; you can redistribute it and/or modify it under the same terms as Perl itself.
```
