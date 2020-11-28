# Introduction

Seafile is an open source cloud storage system with file encryption and group sharing, and emphasis on reliability and high performance.

This repository contains documents for Seafile client.

## LICENSE

This manual is licensed under Apache License v2.0.

## About this manual

The source of this manual is hosted on Github https://github.com/haiwen/seafile-user-manual

## How to compile

You can compile the code in this repository into HTML format by the [mkdocs](https://www.mkdocs.org/) and deploy it to your own web container.

### Install mkdocs

Install the mkdocs package using pip:

```bash
pip install mkdocs
```

### Get the Code

```bash
git clone https://github.com/haiwen/seafile-user-manual.git
```

### Start the server

Make sure you're in the same directory as the mkdocs.yml configuration file, and then start the server by running the mkdocs serve command:

```bash
cd seafile-user-manual
mkdocs serve

INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
```

Open up http://127.0.0.1:8000/ in your browser, and you'll see the seafile manual page being displayed.

### Build the static website


```bash
mkdocs build
```

This will create a new directory, named site. Then you can deploy the '`site`' as a static website.

## Contact information

* Twitter: @seafile https://twitter.com/seafile
* Forum: https://forum.seafile.com
