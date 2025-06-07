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
