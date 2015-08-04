# FAQ

### How to pre-config Seafile in Windows

You can pre-config in Windows via Registry or via `%USERPROFILE%/seafile.ini`

#### Using Registry

To preset the default server address:

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureServerAddr`
- Type: `REG_SZ`
- Value: `<url to the seafile server address>`
```

To preset the account and login token:

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureUsername`
- Type: `REG_SZ`
- Value: `<The Username or Email>`
```

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureUserToken`
- Type: `REG_SZ`
- Value: `<the Seahub access token>` (Not the password)
```

To not allow the user to use any other Seafile server

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureServerAddrOnly`
- Type: `REG_SZ`
- Value: `1` (stands for enable) or `0` (stands for disable)
- Effect: The user can't use any other Seafile server.
```

To preset the location of Seafile folder:

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureDirectory`
- Type: `REG_SZ`
- Value: `<absolute path to the Seafile folder>`
```

To avoid the configuration wizard:

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `HideConfigurationWizard`
- Type: `REG_SZ`
- Value: `0` (show configuration wizard) or `1` (hide configuration wizard)
- Effect: If you run seafile first time or without any account, seafile will look up this configure and hide configure wizard accordingly.
```

To disable the "Do you want to remove the account information" dialog when uninstalling seafile client on Windows

```
- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureKeepConfigWhenUninstall`
- Type: `REG_SZ`
- Value: `0` (show the confirm dialog) or `1` (hide the confirm dialog wizard)
```

> Special Note for 64-bit Windows Deployment: if you are using 64-bit windows
> and using HKLM instead of HKCU to deploy your seafile program. please note you need
> to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile`
> instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`.


#### Using Seafile Configure file (Supported in client 4.3.0+)

Below is a sample:

```
[preconfigure]
PreconfigureDirectory = ~/
PreconfigureUsername = guest@seafile.de
PreconfigureUserToken = t0Ken
PreconfigureServerAddr = https://cloud.seafile.de
```


### How to pre-config Seafile in Mac/Linux

You can use `~/.seafilerc` to pre-config Seafile in Mac/Linux. The options are the same as for Windows.


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

Supported Client: 4.1.0 or later

### How to enable HiDPI support on Linux

You need to build client against Qt 5 (5.4 or later) and set the correct
environment variable before starting client.

- Key: `QT_DEVICE_PIXEL_RATIO`
- Value: `2` (force) or `auto`

Effect: client will show correctly according to screen DPI.

Supported Client: (inofficial) 4.1.0 or later
