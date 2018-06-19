# Install Seafile Client on Linux

* [Ubuntu](#wiki-ubuntu)
* [Debian](#wiki-debian)
* [Fedora](#wiki-fedora)
* [Centos/RHEL](#wiki-centos)
* [Arch Linux](#wiki-archlinux)
* [Linux CLI](#wiki-cli)

## <span id='wiki-ubuntu'>Ubuntu</span>

Ubuntu users can install Seafile client from the [Official PPA](https://code.launchpad.net/~seafile/+archive/ubuntu/seafile-client):

```sh
sudo add-apt-repository ppa:seafile/seafile-client
sudo apt-get update
sudo apt-get install seafile-gui
```

If you only want to install the command-line client, run `sudo apt-get install seafile-cli` instead.

If you want to install the debug symbols (for example, when you want to report a bug), you can install the following packages:

```sh
sudo apt-get install libsearpc-dbg ccnet-dbg libccnet-dbg seafile-daemon-dbg libseafile-dbg seafile-gui-dbg
```

Now you can start seafile client from Unity's dash.

## <span id='wiki-debian'>Debian</span>

Debian users can install Seafile client from our debian repo:

To install the client, first add the signing key:

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 8756C4F765C9AC3CB6B85D62379CE192D401AB61
```

Then add the repo to your apt source list, using the line corresponding to your debian version :

```
# For Debian 7
echo deb http://deb.seadrive.org wheezy main | sudo tee /etc/apt/sources.list.d/seafile.list

# For Debian 8
echo deb http://deb.seadrive.org jessie main | sudo tee /etc/apt/sources.list.d/seafile.list

# For Debian 9
echo deb http://deb.seadrive.org stretch main | sudo tee /etc/apt/sources.list.d/seafile.list
```

Update your local apt cache :

```
sudo apt-get update
```

Now install the client:

```sh
sudo apt-get install seafile-gui
```

If you only want to install the command-line client, run `sudo apt-get install seafile-cli` instead.

## <span id='wiki-fedora'>Fedora (Community Maintained)</span>

There is a *community maintained* Seafile Client RPM package in Fedora's [official repository](https://src.fedoraproject.org/rpms/seafile).

## <span id='wiki-centos'>Centos/RHEL (Community Maintained)</span>

There is a *community maintained* Seafile Client RPM package for CentOS/RHEL https://copr.fedorainfracloud.org/coprs/pkerling/seafile/.

## <span id='wiki-archlinux'>Arch Linux (Community Maintained)</span>

There is a *community maintained* Seafile Client package for Arch Linux:

https://aur.archlinux.org/packages/seafile-client/

## <span id='wiki-cli'>Linux CLI Usage</span>

Please refer to [this documentation](linux-cli.md) for how to use Linux client on a command line server.