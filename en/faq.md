# FAQ

### How to pre-config Seafile directory and server address in Windows

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureServerAddr`
- Type: `REG_SZ`
- Value: `<url to the seafile server address>`

Effect: If you have this value set before starting seafile, seafile will
pick this configure and put it into the server address list used in login dialog
automatically. This configure can be used with or without the below configure.

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureServerAddrOnly`
- Type: `REG_SZ`
- Value: `1` (stands for enable) or `0` (stands for disable)

Effect: If you have this value set before starting seafile, seafile will
pick this configure and lock the server address list used in login dialog
allowing only the preconfigured server address set in the above configure.
automatically. This configure can be only used with the above configure.

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureDirectory`
- Type: `REG_SZ`
- Value: `<absolute path to the seafile data folder>`

Effect: If you run seafile first time and have this configure set before
starting, seafile will pick this configure and create seafile data directory
automatically and start. But if seafile fails to create this data directory,
seafile will refuse to start.

> Value can contains environment variables such as `%USERPROFILE%`

### How to use run Seafile client as a service in Windows

Seafile client can be configured to run as a daemon using tools like Firedaemon. First configure Seafile as the user it should run - in this example "Administator"：


```
Parameters for ccnet: -c C:/Users/Administrator/ccnet
Parameters for seaf-daemon: -c C:/Users/Administrator/ccnet -d S:/seafile-data -w S:/Seafile
```

### How to enable HiDPI support on Windows

The client is built with Qt 5.4 and supports HiDPI if the correct environment
variable is set.

- Key: `QT_DEVICE_PIXEL_RATIO`
- Value: `2` (force) or `auto`

Effect: client will show correctly according to screen DPI.

### How to enable HiDPI support on Linux

You need to build client against Qt 5 (5.4 or later) and set the correct
environment variable before starting client.

- Key: `QT_DEVICE_PIXEL_RATIO`
- Value: `2` (force) or `auto`

Effect: client will show correctly according to screen DPI.
