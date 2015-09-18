# FAQ

- [Preconfigure Seafile Clients](#user-content-preconfigure-main)
  - [Using Windows Registry](#user-content-using-windows-registry)
    - [List of Available Preconfigure Options](#user-content-list-of-preconfigure-options)
  - [Using ~/seafile.ini (windows) or ~/.seafilerc (linux/mac)](#user-content-using-seafile-ini)
- [How to use run Seafile client as a service in Windows](#user-content-run-seafile-client-as-windows-service)
- [Enable HiDPI Support on Windows](#user-content-enable-linux-hidpi-support)
- [Enable HiDPI Support on Linux](#user-content-enable-windows-hidpi-support)

## <a id="preconfigure-main"></a>Preconfigure Seafile Clients

Normally, when the user installs a fresh seafile client, a login dialog would prompt him/her to fill the server address and user credentials. These behavior can be preconfigured by IT admins so that the users don't need to do it themselves.

There are two ways to preconfigure seafile client:

- On windows, the admin can store the details it in the windows registry.
- On all desktop platforms (win/linux/mac), the admin can also store the details in a file `seafile.ini` in the HOME folder of the user.

### <a id="using-windows-registry"></a>Using Windows Registry

The preconfigure information can be stored in one of the following two places:

- `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- or `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`

If the information is found in both places, the one under `HKEY_CURRENT_USER` would take precedence.

**Special Note for 64bit Windows Deployment**

> If you are using 64-bit windows and using HKLM instead of HKCU to deploy your seafile program. please note you need to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile` instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`. This is because seafile client is compiled as a 32-bit application on windows.

#### <a id="list-of-preconfigure-options"></a>List of Available Preconfigure Options

To preset the default server address:

```
- Key: PreconfigureServerAddr
- Type: REG_SZ
- Value: <url to the seafile server address>
```

To preset the account and login token:

```
- Key: PreconfigureUsername
- Type: REG_SZ
- Value: <The Username or Email>
```

```
- Key: PreconfigureUserToken
- Type: REG_SZ
- Value: <the Seahub access token> (You can get the token via Web API)
```

To prevent the user from using any other Seafile server:

```
- Key: PreconfigureServerAddrOnly
- Type: REG_SZ
- Value: 1 (stands for enable) or 0 (stands for disable)
- Effect: The user can't use any other Seafile server.
```

To preset the location of Seafile folder:

```
- Key: PreconfigureDirectory
- Type: REG_SZ
- Value: <absolute path to the Seafile folder>
```

To avoid the configuration wizard:

```
- Key: HideConfigurationWizard
- Type: REG_SZ
- Value: 0 (show configuration wizard) or 1 (hide configuration wizard)
- Effect: If you run seafile first time or without any account, seafile will look up this configure and hide configure wizard accordingly.
```

To disable the "Do you want to remove the account information" dialog when uninstalling seafile client on Windows:

```
- Key: PreconfigureKeepConfigWhenUninstall
- Type: REG_SZ
- Value: 0 (show the confirm dialog) or 1 (hide the confirm dialog wizard)
```

#### <a id="using-seafile-ini"></a>Using ~/seafile.ini (windows) or ~/.seafilerc (linux/mac)

This feature is available in seafile client 4.3.0 and above.

Below is an example to preset server address, user, token and Seafile folder:

```
[preconfigure]
PreconfigureDirectory = ~/
PreconfigureUsername = guest@seafile.de
PreconfigureUserToken = t0Ken
PreconfigureServerAddr = https://cloud.seafile.de
```


### <a id="run-seafile-client-as-windows-service"></a>How to use run Seafile client as a service in Windows

Seafile client can be configured to run as a daemon using tools like Firedaemon. First configure Seafile as the user it should run - in this example "Administator"：


```
Parameters for ccnet: -c C:/Users/Administrator/ccnet
Parameters for seaf-daemon: -c C:/Users/Administrator/ccnet -d S:/seafile-data -w S:/Seafile
```

### <a id="enable-windows-hidpi-support"></a>How to enable HiDPI support on Windows

The client is built with Qt 5.4 and supports HiDPI if the correct environment
variable is set.

- Key: `QT_DEVICE_PIXEL_RATIO`
- Value: `2` (force) or `auto`

Effect: client will show correctly according to screen DPI.

Supported Client: 4.1.0 or later

### <a id="enable-linux-hidpi-support"></a>How to enable HiDPI support on Linux

You need to build client against Qt 5 (5.4 or later) and set the correct
environment variable before starting client.

- Key: `QT_DEVICE_PIXEL_RATIO`
- Value: `2` (force) or `auto`

Effect: client will show correctly according to screen DPI.

Supported Client: (inofficial) 4.1.0 or later
