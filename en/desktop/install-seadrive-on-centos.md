# Install SeaDrive Client on CentOS 7

<p><div class="toc">
<ul>
<li><a href="#wiki-add-repo">Add the Repo</a></li>
<li><a href="#wiki-install">Install SeaDrive Client</a></li>
</ul>
</p>

## <a id="wiki-add-repo"></a> Add the repo

```sh
wget -O- https://git.io/seadrive-centos7-repo | sudo tee /etc/yum.repos.d/seadrive.repo
```

## <a id="wiki-install"></a> Install SeaDrive Client

```sh
sudo yum install -y epel-release
sudo yum install -y seadrive --enablerepo=cr
```

Now you can start SeaDrive Client from the applications menu.
