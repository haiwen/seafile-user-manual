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

## Meaning file syncing errors

File syncing errors are displayed in various places in Seafile desktop clients, including:

- Main window of the Sync client
- File sync error dialog in both Sync client and SeaDrive
- Notification messages

The detailed meaning of these error messages are explained below.

| Error Message                                                                              | Error Meaning                                                                                                                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| “File is locked by another application”，“Folder is locked by another application”          | If these errors occur, it means that the file or directory is being locked by another application, making synchronization impossible. It is possible that a folder being locked is caused by a file inside the folder being opened by another program. You can find the blocking file path in "File sync errors" dialog. Closing the application that opening the file could solve the problem.                                                                                          |
| “File is locked by another user”                                                           | This error indicates that the file may have been locked by another user on the server or by another user via the client.                                                                                                                                                                                                                         |
| “Error when indexing”                                                                      | This error indicates that the client cannot index the file properly, the file may be opened by other applications or by antivirus software. You can find the file path in "File sync errors" dialog. Closing the application that opening the file could solve the problem. You can also add exemption for Seafile client in antivirus software. To trigger syncing for the file again, just update the file.                                                                                                                                                                                          |
| ”Path ends with space or period characte“                                                  | This error indicates that a file name or directory name ending with a space or dot cannot be synchronized to Windows.                                                                                                                                                                                                                            |
| “Path contains invalid characters like ‘\|‘ or ‘:’”                                        | This error indicates that the file or directory name contains illegal characters like '\|' and ':' and cannot be synchronized to Windows.                                                                                                                                                                                                        |
| “Update to file denied by folder permission setting”                                       | This error indicates that the folder has been set with unwritable folder permissions on the server, making it impossible to upload or update files.                                                                                                                                                                                              |
| “Syncing is denied by cloud-only permission settings”                                      | This error indicates that the library or subfolder has non-synchronizable sharing permissions set on the server (e.g. cloud preview), which makes it impossible to synchronize the library to the computer.                                                                                                                                      |
| ”Created or updated a file in a non-writable library or folder“                            | This error indicates that the library or subfolder permissions are not read-write, so the client ignores changes under that folder.                                                                                                                                                                                                              |
| “Permission denied on server”                                                              | This error indicates that the library has been unshared.                                                                                                                                                                                                                                                                                         |
| “Do not have write permission to the library”                                              | This error indicates that the shared permissions of the library are not read-write.                                                                                                                                                                                                                                                              |
| ”internal Server Error“                                                                    | This error indicates that synchronization was not possible due to a server error, usually caused by a library or file on the server that has become corrupted.                                                                                                                                                                                   |
| “Internal data corrupt on the client. Please try to resync the library”                    | This error indicates that the client's metadata has been corrupted, usually due to antivirus software mistakenly deleting the client's metadata. On Windows you need to configure your antivirus software to skip the folder C:\users\username\Seafile\seafile-data, on macOS you need to skip the folder /Users/username/Seafile/.seafile-data. |
| “Failed to write data on the client. Please check disk space or folder permissions”        | This error indicates that the file could not be checked out properly due to incorrect permissions on the local directory or insufficient disk space when the file was downloaded. Both metadata directories and synchronization directories can cause this error.                                                                                |
| “Not enough memor”                                                                         | This error indicates that the computer does not have enough memory, causing the client to fail to allocate memory. Memory allocation may also fail due to other reasons.                                                                                                                                                                         |
| “Concurrent updates to file. File is saved as conflict file”                               | This error indicates that the same file happened to be updated locally when the file was downloaded, and will save the local file as a conflict file.                                                                                                                                                                                            |
| “A folder that may contain not-yet-uploaded files is moved to seafile-recycle-bin folder.” | This error means that when a folder is deleted on the server, there are changes in the folder locally that have not been uploaded, and the folder is moved to the C:\users\username\Seafile\recycle-bin directory on Windows, or to the /Users/username/Seafile/recycle-bin directory on macOS.                                                  |
| “The file path contains symbols that are not supported by the Windows system”              | This error indicates that the macOS or Linux client is uploading files or directory names that contain symbols that are not supported by Windows. This is just a warning that these files will not be synchronized to Windows and will not affect the upload. You can disable this popup in the client configuration.                            |
| “Library cannot be synced since it has too many files.”                                    | This error indicates that the number of files in the library exceeds the maximum number of files that can be synchronized, and the client cannot synchronize such a library.                                                                                                                                                                     |
| “Waiting for confirmation to delete files”                                                 | This error indicates that the number of files deleted locally at one time has exceeded the threshold that requires deletion confirmation, and a deletion confirmation operation is required.By default, more than 500 files need to be deleted at one time. Users can modify this threshold in the client configuration.                         |
| “Files cannot be uploaded to this library due to file number limit settings.”              | This error indicates that the number of files in the library is about to exceed the library's file count limit, and the server is refusing to upload more files.                                                                                                                                                                                 |
| “Failed to upload file blocks. Please check network or firewall”                           | Since the client uploads files in batches, some blocks of files can cause this error when they are not uploaded to the server properly due to network or firewall settings.                                                                                                                                                                      |
| “Path has character case conflict with existing file or folder. Will not be downloaded”    | This error indicates that a file with the same name but a different case has been included locally when the file was downloaded, which is caused by the fact that macOS and Windows are not case-sensitive.                                                                                                                                      |

​
