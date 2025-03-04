# Install Seafile Client on Linux

## Use AppImage

Since 9.0.7 version, we only provide official packages in AppImage format. It can be run on most recent Linux distributions. You can find supported OS versions on <https://cloud.seatable.io/dtable/external-links/a85d4221e41344c19566/?tid=YzYy&vid=pO5i>

You can download `Seafile-x86_64-x.y.z.AppImage` (e.g. `Seafile-x86_64-9.0.7.AppImage`) from [our official website](https://www.seafile.com/en/download/) and give it executable permissionn from the terminal. 

```
chmod +x Seafile-x86_64-9.0.7.AppImage
```

You can also set executable permission for the AppImage file from the GUI. Right click on the AppImage file and choose the "Property" entry. From there you can set executable permission for the file. More details on: <https://discourse.appimage.org/t/how-to-run-an-appimage/80>

You can then double-click `Seafile-x86_64-x.y.z.AppImage` to run it, or run it directly from the terminal.

```
./Seafile-x86_64-9.0.7.AppImage
```

`Seafile-x86_64-x.y.z.AppImage` require FUSE version 2 to run. If your system does not have FUSE installed, please refer to <https://github.com/AppImage/AppImageKit/wiki/FUSE> to install it.

### Desktop Integration

AppImages are standalone bundles, and do not need to be installed. However, some users may want their AppImages to be available like distribution provided applications. Please refer to <https://docs.appimage.org/user-guide/run-appimages.html#ref-desktop-integration> for desktop integration to display AppImage's application icons.

### Auto Update
You can check and update the client using AppImageUpdate. After running AppImageUpdate, select your local Seafile-x86_64-x.y.z.AppImage for the update. AppImageUpdate can be downloaded [here](https://github.com/AppImageCommunity/AppImageUpdate/releases/continuous).

### SSL CA Configuration
Since 9.0.12 version, you can specify the CA path using the environment variable `SEAFILE_SSL_CA_PATH`. When this environment variable is set, seafile client will prioritize reading the CA from the specified path. For example:

```
export SEAFILE_SSL_CA_PATH=/etc/ssl/certs/ca-certificates.crt
./Seafile-x86_64-9.0.12.AppImage
```
Seafile will try to find common paths for CA certificates on various distributions. If it doesn't work, you can set it by this environment variable.

## Installing with package managers (deprecated)

### Debian/Ubuntu

To install the client, first add the signing key:

```
sudo wget https://linux-clients.seafile.com/seafile.asc -O /usr/share/keyrings/seafile-keyring.asc

```

If apt-get reports following error: "The following signatures couldn't be verified because the public key is not available", please update the key for seafile repository.

Then add the repo to your apt source list, using the line corresponding to your Debian/Ubuntu version :

For Debian 9 / Debian 10 / Debian 11 / Ubuntu 18.04 / Ubuntu 20.04 / Ubuntu 22.04
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seafile-deb/$(lsb_release -cs)/ stable main" | sudo tee /etc/apt/sources.list.d/seafile.list > /dev/null

```

Update your local apt cache :

```
sudo apt update

```

Now install the client:

```
sudo apt install -y seafile-gui

```

If you only want to install the command-line client, run `sudo apt-get install seafile-cli` instead.

If you want to install the debug symbols (for example, when you want to report a bug), you can install the following packages:

```sh
sudo apt-get install libsearpc-dbg ccnet-dbg libccnet-dbg seafile-daemon-dbg libseafile-dbg seafile-gui-dbg

```

**note:** from seafile version 7.0.8, seaf-cli only support python3.5 or above on Debian/Ubuntu.

### Fedora

**Note:** You can install directly from the official Fedora repository.

```
sudo dnf install -y seafile-client

```

### Arch Linux (Community Maintained)

There is a _community maintained_ Seafile Client package for Arch Linux:

<https://aur.archlinux.org/packages/seafile-client/>

## Linux CLI Usage

Please refer to [this documentation](linux-cli.md) for how to use Linux client on a command line server.

