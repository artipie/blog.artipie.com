---
layout: post
date: 2020-11-23
title: "Some name"
author: olenagerasimova
description: This blog post shows how binary and pypi repositories can be used.
keywords:
  - artipie
  - private
  - pypi
  - python
  - repository
  - registry
  - binary
---

Being a student I dreamed about something like Artipie, I needed some private centralized storage 
where I could have kept both binary or text data files and Python packages. We were conducting a research
and used to work with a lot of data from experimental measurements and used Python to process and 
visualise them. My university colleagues from that time were mathematicians, they do not have strong
development background and were absolutely fine with passing data and code via flash drive or email.
All my efforts to infiltrate VCS (GitHub, for example, provides free Pro accounts for students 
and professors) and some cloud storage usage were always postponed to the brighter future. I've 
quit the postgraduate program and never saw that future to come.

Now, I'd like to show how I could have used Artipie being that student. In the example I'll use 
[Artipie Central](http://central.artipie.com/), but the same will work with an Artipie instance 
running on your private server in the private network.

## Binary Storage

Artipie can be used as a [storage for any files](https://github.com/artipie/artipie/tree/master/examples/binary), 
this repository I'll use to store experimental data and any measurements results. I've created binary 
`data` repository on Central, exact configuration is the following:
```yaml
repo:
  type: file
  storage: default
  permissions:
    olenagerasimova:
      - upload
      - download
    "*":
      - download
```
Upload is available for me only, but anyone can download the files, more details about permission 
configuration can be found [here](https://github.com/artipie/artipie#repository-permissions).

In this example my data are three text files with some numbers, here is how the first one looks like:
```text
6
3.5
5
4
4.5
3
2.7
5
6
3
1.2
3.2
6
```
The other two files have the same form, only numbers are different. These files can be uploaded to 
the Artipie Central `data` repository with simple `PUT` http request:

```commandline
httpie -a olenagerasimova:*** PUT https://central.artipie.com/olenagerasimova/data/y1.dat @data/y1.dat
```

To download the file use `GET` request

```commandline
httpie -a https://central.artipie.com/olenagerasimova/data/y1.dat > ./data/y1.dat
``` 

or simply open [this](https://central.artipie.com/olenagerasimova/data/y1.dat) link in the browser.

To sum up, this is how I'd use Artipie binary storage to store my research data. As this repository 
API is very simple (http `PUT` and `GET` requests), it's easy to write a peace of code in any language 
to upload and downloads necessary files. What is also important, authorisation is supported in Artipie, 
so it'spossible to grant rights to upload/download from the repository how it suits your case. 

Further we will use these files from Python module to visualise the data.

## Python Storage

Artipie supports [PyPi repository](https://github.com/artipie/artipie/tree/master/examples/pypi), 
so `twine` and `pip` can be used to upload and install Python packages from Artipie. Here is my PyPi 
repository configuration from Central:

```yaml
repo:
  type: pypi
  storage: default
  permissions:
    olenagerasimova:
      - download
      - upload
    "*":
      - download
```

As in the previous example I've allowed download operation to anyone, thus you can install and run 
Python example package with the following command:

```commandline
python3 -m pip install --index-url https://central.artipie.com/olenagerasimova/pypi/ pypiexample
python3 -m pypiexample
``` 

As a result I hope you see a polar plot with three curves, visualisation of our data files. 
Source code is available [here](https://github.com/artipie/pypi-example), the example is very 
simple: it downloads data files from Artipie Central, reads the numbers into arrays and 
uses these arrays to draw the plot. 

TODO: add CD and describe its configuration