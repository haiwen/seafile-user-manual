# 安装 Seafile Linux 客户端

<p><div class="toc">
<ul>
<li><a href="#wiki-ubuntu">Ubuntu</a></li>
<li><a href="#wiki-ubuntu">Debian</a></li>
<li><a href="#wiki-ubuntu">Fedora</a></li>
</ul>
</p>

## <a id="wiki-ubuntu"></a> Ubuntu

Ubuntu 用户可以从 [Seafile 官方 PPA](https://code.launchpad.net/~seafile/+archive/ubuntu/seafile-client) 中安装:

```sh
sudo apt-add-repository ppa:seafile/seafile-client
sudo apt-get update
sudo apt-get install seafile-gui
```

如果你只需要命令行客户端，则只需要运行 `sudo apt-get install seafile-cli` 即可。

安装完成后，你就可以从 Unity 的 dash 中启动 seafile 客户端了。

## <a id="wiki-debian"></a> Debian

Debian 用户可以从 Seafile 的 官方源中安装:

首先添加签名公钥:

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 8756C4F765C9AC3CB6B85D62379CE192D401AB61
```

然后添加更新源, 这里我们以 Debian 8 (jessie) 为例，如果你使用 Debian 7, 请把相应的字段替换为 "wheezy".

```
echo deb http://deb.seadrive.org jessie main | sudo tee /etc/apt/sources.list.d/seafile.list
sudo apt-get update
```

安装 Seafile 客户端:

```sh
sudo apt-get install seafile-gui
```

如果你只需要命令行客户端，则只需要运行 `sudo apt-get install seafile-cli` 即可。

## <a id="wiki-fedora"></a> Fedora (由社区维护)

Fedora 官方源中有一个由 *社区维护* 的 Seafile 客户端 RPM 包, 详见 [Fedora Seafile 客户端页面](https://admin.fedoraproject.org/pkgdb/package/rpms/seafile/).
