## Environment
- Tested on Ubuntu 20.04.01

### Enable required config options

Enable kernel config options required for syzkaller as described [here](kernel_configs.md).
It's not required to enable all of them, but at the very least you need:

``` make
# Coverage collection.
CONFIG_KCOV=y

# Debug info for symbolization.
CONFIG_DEBUG_INFO_DWARF4=y

# Memory bug detector
CONFIG_KASAN=y
CONFIG_KASAN_INLINE=y

# Required for Debian Stretch and later
CONFIG_CONFIGFS_FS=y
CONFIG_SECURITYFS=y

# Required for fuzzing nftables
CONFIG_NF_TABLES=y
```


## Installation

~~~~{.sh}
# chekcout commit version
$ git checkout 0ea90952bdac100bde3149fa2a7818ba7af943b4

```
wget https://dl.google.com/go/go1.22.1.linux-amd64.tar.gz
tar -xf go1.22.1.linux-amd64.tar.gz
export GOROOT=`pwd`/go
export PATH=$GOROOT/bin:$PATH
```

To download and build `NFsyzkaller`:

``` bash
git clone https://github.com/google/syzkaller
cd NFsyzkaller
make
```

~~~~
