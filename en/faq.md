# FAQ

## Preconfigure Seafile Clients

Normally, when the user installs a fresh seafile client, a login dialog would prompt him/her to fill the server address and user credentials. These behavior can be preconfigured by IT admins so that the users don't need to do it themselves.

There are two ways to preconfigure seafile client:

* On windows, the admin can store the details it in the windows registry.
* On all desktop platforms (win/linux/mac), the admin can also store the details in a file `seafile.ini` in the HOME folder of the user.

### Preconfigure options for sync clients

#### Using Windows Registry

The preconfigure information can be stored in one of the following two places:

* `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
* or `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`

If the information is found in both places, the one under `HKEY_CURRENT_USER` would take precedence.

**Special Note for 64bit Windows Deployment**

> For client version < 8.0, if you are using 64-bit windows and using HKLM instead of HKCU to deploy your seafile program. please note you need to correct the PrimaryKey to `HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Seafile` instead of `HKEY_LOCAL_MACHINE\\SOFTWARE\\Seafile`. This is because seafile client is compiled as a 32-bit application on windows.
> This restriction no longer applies to version 8.0 or newer. The client has been compiled as a 64-bit application since 8.0.

List of Available Preconfigure Options.

To preset the default server address:

```
- Key: PreconfigureServerAddr
- Type: REG_SZ
- Value: <url to the seafile server address>

```

To preset the default shibboleth login address:

```
- Key: PreconfigureShibbolethLoginUrl
- Type: REG_SZ
- Value: <the shibboleth login url>, e.g https://example.seafile.com/shib-login

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

When the user installs seafile client on windows, the seafile client program would be started immediately after the installation is finished.

While this is the expected action for most users, it may be necessary to disable it sometimes. For example, when the seafile client is installed with Windows Group Policy Object (GPO), the program would be launched with the ADMIN user (instead of the current login user), which would make the program work incorrectly. In such cases, it's desirable to disable the launch of seafile client after installation.

To disable this behavior:

```
- Key: PreconfigureSuppressLaunchAfterInstall
- Type: REG_SZ
- Value: 1

```

Since version 7.0.6, you may use the option below to control average block size for indexing files in Sync client. **Please note that, after setting this option in registry, you have to restart the sync client twice to let the option take effect.**

```
- Key: PreconfigureBlockSize
- Type: REG_SZ
- Value: a value larger than 1024. The unit is in bytes.

```

#### Using ~/seafile.ini (windows) or ~/.seafilerc (linux/mac)

This feature is available in seafile client 4.3.0 and above.

Below is an example to preset server address, user, token and Seafile folder:

```
[preconfigure]
PreconfigureDirectory = ~/
PreconfigureUsername = guest@seafile.de
PreconfigureUserToken = t0Ken
PreconfigureServerAddr = https://cloud.seafile.de

```

### Preconfigure options for SeaDrive

#### Using Windows Registry

From SeaDrive 2.0.6 on, some preconfigure registry keys are supported.

The preconfigure information can be stored in one of the following two places:

* `HKEY_CURRENT_USER\\SOFTWARE\\SeaDrive`
* or `HKEY_LOCAL_MACHINE\\SOFTWARE\\SeaDrive`

If the information is found in both places, the one under `HKEY_CURRENT_USER` would take precedence.

Below options are provided. You can refer to sync client's documentation about the meaning of each option.

* PreconfigureServerAddr
* PreconfigureServerAddrOnly
* PreconfigureUserName
* PreconfigureUserToken
* PreconfigureShibbolethLoginUrl
* HideConfigurationWizard
* PreconfigureKeepConfigWhenUninstall
* PreconfigureSuppressLaunchAfterInstall

In 2.0.13 version, a preconfigure option PreconfigureCacheDirectory is added. It can be used to preset the cache folder location.

## How to use run Seafile client as a service on Windows

Seafile client can be configured to run as a daemon using tools like Firedaemon. First configure Seafile as the user it should run - in this example "Administator"：

```
Parameters for ccnet: -c C:/Users/Administrator/ccnet
Parameters for seaf-daemon: -c C:/Users/Administrator/ccnet -d S:/seafile-data -w S:/Seafile

```

Replace `S:` with the partition you actually use to store `seafile-data` and `Seafile` folder.

You call also use tools like NSSM (the Non-Sucking Service Manager). For more information, please check <https://valdasv.blogspot.jp/2016/06/seafile-client-service.html>

## How to solve the shell icon overlay not shown problem

Windows uses only the first 15 of the entries in the registry 
(HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Explorer\\ShellIconOverlayIdentifiers). If there are other programs, like Dropbox and OneDrive, use up the overlay icons, Seafile shell icon overlay will not shown. To solve the problem, just delete the registration entries of other programs.
