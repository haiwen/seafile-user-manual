# Seafile client for a Cli server

## Installation

You can follow [this documentaion](install_linux_client.md) to install Seafile CLI client on various Linux distributions.

## Basic Usage

Initialise & start the client

```sh
# choose a folder where to store the seafile client settings e.g ~/seafile-client
mkdir ~/seafile-client            # create the settings folder
seaf-cli init -d ~/seafile-client  # initialise seafile client with this folder
seaf-cli start
```

Download a library from a server

* retrieve the library id by browsing on the server -> it's in the url after `/repo/`
* then

```sh
seaf-cli download -l "the id of the library" -s  "the url + port of server" -d "the folder where the library folder will be downloaded" -u "username on server" [-p "password"]
seaf-cli status  # check status of ongoing downloads
# Name  Status  Progress
# Apps    downloading     9984/10367, 9216.1KB/s
```

Note: if you not supply the password parameter in the command, it will be asked later, which is more safe.

Example: `seaf-cli download -l 0536c006-8a43-449e-8718-39f12111620d -s http://cloud.seafile.com -d /tmp -u freeplant@test.com`

Download a library from a server and sync with an existing folder.

```sh
# This is the same as download : replace download by sync 
seaf-cli sync -l "the id of the library" -s  "the url + port of server" -d "the folder where the library will be synced with" -u "username on server" -p "password"
```


## Man documentation

seaf-cli is command line interface for seafile client.

Subcommands:

```
    init                Initialize config directory
    start               Start ccnet and seafile daemon
    stop                Stop ccnet and seafile daemon
    list                List local libraries
    list-remote         List remote libraries
    status              Show syncing status
    download            Download a library from seafile server
    download-by-name    Download a library defined by name from seafile server
    sync                Sync a library with an existing foler
    desync              Desync a library with seafile server
    create              Create a library
    config              Configure seafile client
```

Running `seaf-cli -h` will show the above help. For each subcommand, you can also use `-h` option to get help, e.g. `seaf-cli download -h`.

Detail
======

Seafile client stores all its configure information in a config dir. The default location is `~/.ccnet`. All the commands below accept an option `-c <config-dir>`.

init
----
Initialize seafile client. This command initializes the config dir. It also creates sub-directories `seafile-data` and `seafile` under `parent-dir`. `seafile-data` is used to store internal data, while `seafile` is used as the default location put downloaded libraries.

```
seaf-cli init [-c <config-dir>] -d <parent-dir>
```

A file named `seafile.ini` will be created under `~/.ccnet` to record the location of `seafile-data` directory.

If you want to run multiple instances of Seafile cli client in the same machine, you can specify different `config-dir` and `parent-dir` when initializing different client instances. Then the instances can run without interfering each others. When starting the instances, just specify ccnet config directories with the `-c` option.

start
-----
Start seafile client. This command start `ccnet` and `seaf-daemon`, `ccnet` is the network part of seafile client, `seaf-daemon` manages the files.

```
seaf-cli start [-c <config-dir>]
```

stop
----
Stop seafile client.

```
seaf-cli stop [-c <config-dir>]
```

Download
--------
Download a library from seafile server

```
seaf-cli download -l <library-id> -s <seahub-server-url> -d <parent-directory> -u <username> [-p <password>]
```

sync
----
Synchronize a library with an existing folder.

```
seaf-cli sync -l <library-id> -s <seahub-server-url> -d <existing-folder> -u <username> [-p <password>]
```

desync
------
Desynchronize a library from seafile server

```
seaf-cli desync -d <existing-folder>
```

create
------
Create a new library on server

```
seaf-cli create [-h] -n library-name -t description [-e library-password] -s server -u username -p password
```

## Skip SSL certificate verify 

If you're using self-signed certificate on the server, you should ask the client to skip verifying certificate.

```
seaf-cli config -k disable_verify_certificate -v true
```

## Set Transfer Speed Limit

Set upload speed limit to 1MB/s :

```sh
seaf-cli config -k upload_limit -v 1000000
```

Set download speed limit to 1MB/s :

```sh
seaf-cli config -k download_limit -v 1000000
```

## Two factor authentication

Now, the seaf-cli has suported 'Two Factor Authentication'.
If you want to use the feature, you should add the argument `--tfa <token>` to any `seaf-cli` commands.

For example:

```sh
seaf-cli start --tfa <token> [-c <config-dir>]
```
