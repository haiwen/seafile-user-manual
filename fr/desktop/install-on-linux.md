# Installer le client Seafile sur Linux

<p><div class="toc">
<ul>
<li><a href="#wiki-ubuntu">Ubuntu</a></li>
<li><a href="#wiki-ubuntu">Debian</a></li>
<li><a href="#wiki-ubuntu">Fedora</a></li>
<li><a href="#wiki-centos">Centos/RHEL</a></li>
<li><a href="#wiki-archlinux">Arch Linux</a></li>
<li><a href="#wiki-cli">Linux CLI</a></li>
</ul>
</p>

## <a id="wiki-ubuntu"></a> Ubuntu

## Ubuntu 17.10, 18.04 et plus récentes

Seafile est disponible directement dans Ubuntu, en le cherchant dans Logiciels. <a href="apt:seafile-gui">apt:seafile-gui</a>.

## Anciennes version d'Ubuntu (17.04 et plus anciennes)

Les utilisatrices·teurs d'Ubuntu peuvent installer le client Seafile depuis le [PPA officiel](https://code.launchpad.net/~seafile/+archive/ubuntu/seafile-client) :

```sh
sudo add-apt-repository ppa:seafile/seafile-client
sudo apt-get update
sudo apt-get install seafile-gui
```

Si vous voulez installer uniquement le client en ligne de commande, lancez `sudo apt-get install seafile-cli` à la place.

Vous pouvez désormais lancer le client Seafile depuis le dash d'Unity. 

## <a id="wiki-debian"></a> Debian

### Debian 9 (Stretch)
Si vous utilisez Debian 9 (Stretch), Seafile est disponible dans les [dépôts Backports](https://backports.debian.org/Instructions/).

Pour ajouter les backports, lancez (en étant connecté en *root*) :

```sh
echo deb http://ftp.debian.org/debian stretch-backports main | tee /etc/apt/sources.list.d/backports.list
apt update
```

Puis, pour installer Seafile :

```sh
apt-get -t stretch-backports install seafile-gui
```

### Debian 8 (Jessie)

Les utilisatrices·teurs des anciennes version de Debian peuvent installer le client Seafile depuis notre [dépôt Bintray officiel](https://bintray.com/seafile-org/deb).

Pour installer le client, ajoutez d'abord la clef de chiffrement de Bintray :

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 8756C4F765C9AC3CB6B85D62379CE192D401AB61
```

Ensuite ajoutez le dépôt à la liste de vos sources APT, ici nous utilisons Debian 8 (jessie) comme exemple, changez le pour "wheezy" si vous utilisez Debian 7. 

```
echo deb http://deb.seadrive.org jessie main | sudo tee /etc/apt/sources.list.d/seafile.list
sudo apt-get update
```

Ensuite, installez le client :

```sh
sudo apt-get install seafile-gui
```

Si vous voulez n'installer que le client en ligne de commande, lancez `sudo apt-get install seafile-cli` à la place.

## <a id="wiki-fedora"></a> Fedora (Maintenu par la communauté)

Il y a un paquet RPM du client Seafile maintenu par la communauté dans le [dépôt officiel de Fedora](https://admin.fedoraproject.org/pkgdb/package/rpms/seafile/).

## <a id="wiki-centos"></a> CentOS/RHEL (Maintenu par la communauté)

Il y a un paquet RPM du client Seafile maintenu par la communauté pour CentOS/RHEL https://copr.fedorainfracloud.org/coprs/pkerling/seafile/.

## <a id="wiki-archlinux"></a> Arch Linux (Maintenu par la communauté)

Il y a un paquet maintenu par la communauté pour Arch Linux :

https://aur.archlinux.org/packages/seafile-client/

## <a id="wiki-cli"></a> Utilisation en ligne de commande du client Linux

Consultez [cette documentation](linux-cli.md) pour des instruction sur l'utilisation du client en ligne de commande pour Linux.
