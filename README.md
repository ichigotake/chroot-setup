# NAME

chroot-setup - [WIP] Set up utility for chroot(2)

## SYNOPSYS

```sh
$ chroot-setup [directory] [sub_command] [args...]
```

## COMMAND

### add

```sh
$ chroot-setup add my-container /usr/bin/env
$ ls ./my-container
```

### new

```sh
$ chroot-setup new /path/to/my-container
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

## LICENSE

Copyright (C) ichigotake

This library is free software; you can redistribute it and/or modify it under the same terms as Perl itself.
