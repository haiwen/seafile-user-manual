# 常见问题

### 如何在Windows中预配置Seafile路径和服务器地址

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureServerAddr`
- Type: `REG_SZ`
- Value: `<url to the seafile server address>`

注意：如果在启动Seafile之前设置了它，Seafile会自动读取配置信息并显示在登录对话框中的账户列表里。该配置可以结合下面的配置使用，也可以忽略下面的配置。

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureServerAddrOnly`
- Type: `REG_SZ`
- Value: `1` (stands for enable) or `0` (stands for disable)

注意：如果在启动Seafile之前设置了它，Seafile会自动读取配置信息并锁定显示在登录对话框中的服务器地址列表从而只显示预先配置的服务器地址。此配置只能结合上面的配置使用。

- PrimaryKey: `HKEY_CURRENT_USER\\SOFTWARE\\Seafile`
- Key: `PreconfigureDirectory`
- Type: `REG_SZ`
- Value: `<absolute path to the seafile data folder>`

注意：如果你是第一次运行Seafile并且在启动前完成了配置，Seafile会自动读取配置信息，创建Seafile目录并启动。如果创建目录失败，Seafile会停止启动。

> Value can contains environment variables such as `%USERPROFILE%`

### 如何在Windows中使 Seafile 以后台服务形式运行

可以使用Firedaemon工具把Seafile客户端配置成以daemon的形式运行。首先把Seafile配置成它应该运行的账户-在这个例子中是“Administator”账户：


```
Parameters for ccnet: -c C:/Users/Administrator/ccnet
Parameters for seaf-daemon: -c C:/Users/Administrator/ccnet -d S:/seafile-data -w S:/Seafile
```


