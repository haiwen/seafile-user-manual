# Install Seafile Client on Linux

You can find supported OS versions on <https://cloud.seatable.io/dtable/external-links/a85d4221e41344c19566/?tid=YzYy&vid=pO5i>

## Debian/Ubuntu

To install the client, first add the signing key:

```
sudo wget https://linux-clients.seafile.com/seafile.asc -O /usr/share/keyrings/seafile-keyring.asc

```

Then add the repo to your apt source list, using the line corresponding to your Debian/Ubuntu version :

```
For Debian 9
sudo bash -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seafile-deb/stretch/ stable main' > /etc/apt/sources.list.d/seafile.list"

```

```
For Debian 10
sudo bash -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seafile-deb/buster/ stable main' > /etc/apt/sources.list.d/seafile.list"

```

```
For Ubuntu 18.04
sudo bash -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seafile-deb/bionic/ stable main' > /etc/apt/sources.list.d/seafile.list"

```

```
For Ubuntu 20.04
sudo bash -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seafile-deb/focal/ stable main' > /etc/apt/sources.list.d/seafile.list"

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

## Centos 7

Since 7.0.3 version, we provide official repo for CentOS or RHEL. Currently only CentOS/RHEL 7 is supported.

Add the repo

```
sudo cat > /etc/yum.repos.d/seafile.repo <<EOF
[seafile]
name=seafile
baseurl=https://linux-clients.seafile.com/seafile-rpm/centos7
gpgcheck=0
enabled=1
EOF

```

Install Seafile Client

```
sudo yum install -y epel-release

sudo yum install -y seafile --enablerepo=cr

```

## Fedora

Since 7.0.9 version, we provide official repo for Fedora. Currently Fedora 31 and Fedora 32 is supported.

Add the repo

```
sudo cat > /etc/yum.repos.d/seafile.repo <<EOF
[seafile]
name=seafile
baseurl=https://linux-clients.seafile.com/seafile-rpm/fedora32
gpgcheck=0
enabled=1
EOF

```

For fedora 31, The `baseurl` above should be replaced with `https://linux-clients.seafile.com/seafile-rpm/fedora31`

Install Seafile Client

```
sudo yum install -y seafile

```

## Arch Linux (Community Maintained)

There is a _community maintained_ Seafile Client package for Arch Linux:

<https://aur.archlinux.org/packages/seafile-client/>

## Linux CLI Usage

Please refer to [this documentation](linux-cli.md) for how to use Linux client on a command line server.
