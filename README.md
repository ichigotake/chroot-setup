# NAME

chroot-setup - [WIP] Set up utility for chroot(8)

## SYNOPSYS

```sh
$ chroot-setup [directory] [sub_command] [args...]
```

## COMMAND

### add

```sh
$ chroot-setup add /path/to/my-container /usr/bin/env
$ ls -l /path/to/my-container/usr/bin/env
-rw-r--r--  1 ichigotake  staff  14224  8 31 13:49 /path/to/my-container/usr/bin/env
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
