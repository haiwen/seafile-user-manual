# Introduction

Seafile is an open source cloud storage system with file encryption and group sharing, and emphasis on reliability and high performance.

This repository contains documents for Seafile client.

## LICENSE

This manual is licensed under Apache License v2.0.

## About this manual

The source of this manual is hosted on Github https://github.com/haiwen/seafile-user-manual

## How to compile

You can compile the code in this repository into HTML format by the [GitBook](https://www.gitbook.com/) and deploy it to your own web container.

### Install gitbook

The best way to install GitBook is via NPM. At the terminal prompt, simply run the following command to install GitBook:

- For Ubuntu

```bash
apt-get install npm -y
npm install gitbook-cli -g
```

- For CentOS

```bash
yum install npm -y
npm install gitbook-cli -g
```

### Get the Code

```bash
git clone https://github.com/haiwen/seafile-user-manual.git
```

### Build the static website

```bash
cd seafile-user-manual
gitbook init
gitbook build # Will generate a '_book' directory in the current directory
```

Then you can deploy the '`_book`' as a static website.

Eg: Nginx

```bash
cp -r ./_book /var/www/gitbook
# Modified the nginx configuration file: "root /var/www/gitbook;"
# And than
nginx -s reload
```

## Contact information

* Twitter: @seafile https://twitter.com/seafile
* Forum: https://forum.seafile.com
