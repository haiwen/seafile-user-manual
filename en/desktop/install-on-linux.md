# Install Seafile Client on Linux

<p><div class="toc">
<ul>
<li><a href="#wiki-ubuntu">Ubuntu</a></li>
<li><a href="#wiki-debian">Debian</a></li>
<li><a href="#wiki-fedora">Fedora</a></li>
<li><a href="#wiki-centos">Centos/RHEL</a></li>
<li><a href="#wiki-archlinux">Arch Linux</a></li>
</ul>
</p>

## <a id="wiki-ubuntu"></a> Ubuntu

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

## <a id="wiki-debian"></a> Debian

Debian users can install Seafile client from our [Official Bintray Repo](https://bintray.com/seafile-org/deb).

To install the client, first add bintray's signing key:

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 8756C4F765C9AC3CB6B85D62379CE192D401AB61
```
Then add the repo to your apt source list, here we use Debian 8 (jessie) as an example, so change it to "wheezy" if you're using Debian 7.

```
echo deb http://dl.bintray.com/seafile-org/deb jessie main | sudo tee /etc/apt/sources.list.d/seafile.list
sudo apt-get update
```

Now install the client:

```sh
sudo apt-get install seafile-gui
```

If you only want to install the command-line client, run `sudo apt-get install seafile-cli` instead.

## <a id="wiki-fedora"></a> Fedora (Community Maintained)

There is a *community maintained* Seafile Client RPM package in Fedora's [official repository](https://admin.fedoraproject.org/pkgdb/package/rpms/seafile/).

## <a id="wiki-centos"></a> CentOS/RHEL (Community Maintained)

There is a *community maintained* Seafile Client RPM package for CentOS/RHEL https://copr.fedorainfracloud.org/coprs/pkerling/seafile/.

## <a id="wiki-archlinux"></a> Arch Linux (Community Maintained)

There is a *community maintained* Seafile Client package for Arch Linux:

https://aur.archlinux.org/packages/seafile-client/
