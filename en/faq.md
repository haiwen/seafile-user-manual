# FAQ

### How to pre-config Seafile default account

##### Using Registry (windows only):

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureServerAddr`
- Type: `REG_SZ`
- Value: `<url to the seafile server address>`

##### Using Seafile Configure file

- Configure File: `%USERPROFILE%/seafile.ini` (windows) or `~/.seafilerc` (others)
- Group: `preconfigure`
- Key: `PreconfigureServerAddr`
- Type: String
- Value: `<url to the seafile server address>`

Beside the `PreconfigureServerAddr` (required), you will need to set up
`PreconfigureUsername` (required), `PreconfigureUserToken` (required)
and `PreconfigureComputerName` (optional) to activate the automatic login which
happens when the seafile client runs first time.

Below is a sample:
```
[preconfigure]
PreconfigureDirectory = ~/
PreconfigureUsername = guest@seafile.de
PreconfigureUserToken = t0Ken
PreconfigureServerAddr = https://cloud.seafile.de
```

Effect: If you have this server address value set before starting seafile,
seafile will pick this configure and put it into the server address list used in
login dialog automatically. This configure can be used with or without the below
configure. In additional, if you have username, access token, server address set
up correctly according to the above note, seafile will trigger an automatic
attempt to login to add the default account.

Supported Client: 4.3.0 or later

> Special Note for 64-bit Windows Deployment: if you are using 64-bit windows
> and using HKLM instead of HKCU to deploy your seafile program. please note you need
> to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile`
> instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`.

### How to pre-config Seafile directory

##### Using Registry (windows only):

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureServerAddrOnly`
- Type: `REG_SZ`
- Value: `1` (stands for enable) or `0` (stands for disable)

##### Using Seafile Configure file

- Configure File: `%USERPROFILE%/seafile.ini` (windows) or `~/.seafilerc` (others)
- Group: `preconfigure`
- Key: `PreconfigureServerAddrOnly`
- Type: Integer
- Value: `1` (stands for enable) or `0` (stands for disable)

Effect: If you have this value set before starting seafile, seafile will
pick this configure and lock the server address list used in login dialog
allowing only the preconfigured server address set in the above configure.
automatically. This configure can be only used with the above configure.

Supported Client: 4.2.9 or later

> Special Note for 64-bit Windows Deployment: if you are using 64-bit windows
> and using HKLM instead of HKCU to deploy your seafile program. please note you need
> to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile`
> instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`.

##### Using Registry (windows only):

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureDirectory`
- Type: `REG_SZ`
- Value: `<absolute path to the seafile data folder>`

##### Using Seafile Configure file

- Configure File: `%USERPROFILE%/seafile.ini` (windows) or `~/.seafilerc` (others)
- Group: `preconfigure`
- Key: `PreconfigureDirectory`
- Type: String
- Value: `<absolute path to the seafile data folder>`

Effect: If you run seafile first time and have this configure set before
starting, seafile will pick this configure and create seafile data directory
automatically and start. But if seafile fails to create this data directory,
seafile will refuse to start.

Supported Client: 4.3.0 or later

> Special Note for 64-bit Windows Deployment: if you are using 64-bit windows
> and using HKLM instead of HKCU to deploy your seafile program. please note you need
> to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile`
> instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`.

> Value can contains environment variables such as `%USERPROFILE%`

### How to pre-config Seafile to avoid configuration wizard in Windows

##### Using Registry (windows only):

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `HideConfigurationWizard`
- Type: `REG_SZ`
- Value: `0` (show configuration wizard) or `1` (hide configuration wizard)

##### Using Seafile Configure file

- Configure File: `%USERPROFILE%/seafile.ini` (windows) or `~/.seafilerc` (others)
- Group: `preconfigure`
- Key: `HideConfigurationWizard`
- Type: Integer
- Value: `0` (show configuration wizard) or `1` (hide configuration wizard)

Effect: If you run seafile first time or without any account, seafile will look
up this configure and hide configure wizard accordingly.

Supported Client: 4.3.0 or later

> Special Note for 64-bit Windows Deployment: if you are using 64-bit windows
> and using HKLM instead of HKCU to deploy your seafile program. please note you need
> to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile`
> instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`.

> It is better to use it with `PreconfigureServerAddr` configuration

### How to disable the "Do you want to remove the account information" dialog when uninstalling seafile client on Windows

##### Using Registry:

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile` ( or `HKEY_LOCAL_MACHINE` )
- Key: `PreconfigureKeepConfigWhenUninstall`
- Type: `REG_SZ`
- Value: `0` (show the confirm dialog) or `1` (hide the confirm dialog wizard)

##### Using Seafile Configure file

- Configure File: `%USERPROFILE%/seafile.ini`:
- Group: `preconfigure`
- Key: `PreconfigureKeepConfigWhenUninstall`
- Type: Integer
- Value: `0` (show configuration wizard) or `1` (hide configuration wizard)

Effect: When the user uninstalls the seafile windows client, normally he would see a dialog asking "Do you want to remove the account information?". If this configuration is set to `1`, the dialog won't come out, and the account information would not be removed.

Supported Client: 4.3.0 or later

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
