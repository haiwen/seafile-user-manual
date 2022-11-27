# Using Seafile Drive Client on Linux

You can find supported OS versions on <https://cloud.seatable.io/dtable/external-links/a85d4221e41344c19566/?tid=YzYy&vid=pO5i>

## Installing on Debian/Ubuntu

To install the client, first add the signing key:

```
sudo wget https://linux-clients.seafile.com/seafile.asc -O /usr/share/keyrings/seafile-keyring.asc

```

If apt-get reports following error: "The following signatures couldn't be verified because the public key is not available", please update the key for seafile repository.

Then add the repo to your apt source list, using the line corresponding to your Debian/Ubuntu version :

For Debian 9 / Debian 10 / Debian 11 / Ubuntu 18.04 / Ubuntu 20.04 / Ubuntu 22.04
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/seafile-keyring.asc] https://linux-clients.seafile.com/seadrive-deb/$(lsb_release -cs)/ stable main" | sudo tee /etc/apt/sources.list.d/seadrive.list > /dev/null

```

Update your local apt cache :

```
sudo apt update

```

To install SeaDrive with GUI:

```
sudo apt-get install seadrive-gui

```

To install SeaDrive without GUI:

```
sudo apt-get install seadrive-daemon

```

## Centos 7

Since 7.0.3 version, we provide official repo for CentOS or RHEL. Currently only CentOS/RHEL 7 is supported.

Add the repo (The same repo is used for seadrive.)

```
sudo cat > /etc/yum.repos.d/seadrive.repo <<EOF
[seadrive]
name=seadrive
baseurl=https://linux-clients.seafile.com/seadrive-rpm
gpgcheck=0
enabled=1
EOF

```

Install SeaDrive Client

```
sudo yum install -y epel-release
sudo yum install -y seadrive --enablerepo=cr

```

## Fedora

**Note:** You can install directly from the official Fedora repository.

```
sudo dnf install -y seadrive-gui

```

## Running SeaDrive with GUI

To use SeaDrive, just run "SeaDrive" from your desktop environment, or type "seadirve-gui" in command line. After logging into your server, the virtual drive will be mounted in `~/SeaDrive.`

## Running SeaDrive without GUI

In some use cases, it is useful to run SeaDrive in a server environment. To use SeaDrive without GUI, you can directly run seadrive-daemon (the background daemon) from command line.

First, you have to obtain an access token from your server.

```
curl -d "username=username@example.com" -d "password=123456" https://seafile.example.com/api2/auth-token/

```

Then you have to prepare a config file for SeaDrive. Let's assume that you save the config file as `~/seadrive.conf.`

```
[account]
server = https://seafile.example.com
username = username@example.com
token = 3131a3a93156f80bc86aa9f12cf794e0364ed57b
is_pro = true

[general]
client_name = johns-ubuntu

[cache]
size_limit = 10GB
clean_cache_interval = 10

```

You can only specify one account in the config file. If you need to switch accounts, you'll have to stop SeaDrive, change config file and restart. Meaning of config options are as following:

* token: The access token you obtained above.
* is_pro: Set to true if your server is Pro edition.
* client_name: This name will be displayed in the device information on the server.
* size_limit: Size limit of local cache space.
* clean_cache_interval: Interval of cache cleaning. The unit is minute.

Then you can start seadrive:

```
seadrive -c ~/seadrive.conf -f -d data-directory [-l logfile] virtual-drive-dir

```

Note that you must give `-f` option in the command line, to make sure seadrive runs in foregound, instead of forking as a daemon. By default, the data directory used by the SeaDrive GUI client will be `~/.seadrive/data`. It's recommended to use this path for data directory to be consistent with the GUI client. The log file path is `~/.seadrive/logs/seadrive.log`.

Sometimes you'll see the following error:

```
fuse: bad mount point `/home/user/SeaDrive': Transport endpoint is not connected

```

You can run `fusermount -u /home/user/SeaDrive` to fix the problem.


