## Package management

### ZYpp (package manager for SUSE-Linux, equivalent to apt for ubuntu)

refresh meta data of packages
```bash
zypper refresh
```

install package
```bash
zypper install <package_name>
```

remove package
```bash
zypper remove <package_name>
```

show all available updates
```bash
zypper list-updates
```

update all packages
```bash
zypper update
```

update a package
```bash
zypper update <package>
```

show a package info
```bash
zypper info <package>
```

search a package by name
```bash
zypper search <package_name>
```

list installed packages
```bash
zypper packages --installed-only
```

**Note:** official SUSE packages are called patches, external sources (e.g. packman) are using the update mechanism

install all needed patches	
```bash
zypper patch
```

Show patch status	
```bash
zypper patch-check
```


### APT (package manager for Debian, Ubuntu)

refresh meta data of packages
```bash
apt update
```

install package
```bash
apt install <package_name>
```

upgrades all packages
```bash
apt upgrade
```

upgrades all packages and removes packages, if necessary
```bash
apt full-upgrade
```

remove package
```bash
apt remove <package_name>
```

remove all packages, that are no longer needed
```bash
apt autoremove
```

delete packages from the cache
```bash
apt autoclean
```

list all available packages
```bash
apt list
```

list all installed packages
```bash
apt list --installed
```

search for a package
```bash
apt search <name>
```

show information for a package
```bash
apt show <package_name>
```

equivalent to apt full-upgrade
```bash
apt-get dist-upgrade
```
