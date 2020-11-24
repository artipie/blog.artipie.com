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
visualise them. My university colleagues from that time were mathematicians, they did not have strong
development background and were absolutely fine with passing data and code via flash drive or email.
All my efforts to inculcate VCS (GitHub, for example, provides free Pro accounts for students 
and professors) and some cloud storage usage were always postponed to the brighter future. I've 
quit the postgraduate program and never saw that future to come.

Now, I'd like to show how I could have used Artipie being that student. In the example I'll use 
[Artipie Central](http://central.artipie.com/), but the same will work with an Artipie instance 
running on your private server in the private network.

## Python Repository

Artipie supports [PyPi repository](https://github.com/artipie/artipie/tree/master/examples/pypi) which
`twine` and `pip` can perfectly understand. This means that you can work with Artipie Python 
repository exactly as you do while installing or publishing packages from or to [PyPI](https://pypi.org/) 
and [TestPyPI](https://test.pypi.org/) repos. Here is my PyPi repository configuration from 
Artipie Central:

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

Upload is available for me only, but anyone can download any package, more details about permission 
configuration can be found [here](https://github.com/artipie/artipie#repository-permissions). 

To make sure this repository exists and works, open [index page](https://central.artipie.com/olenagerasimova/pypi) 
from your browser, packages list should be displayed there.

I've created a small Python example project, source code is available [here](https://github.com/artipie/pypi-example), 
the main idea of the example is from my university times: download three data files from Artipie Central 
(the next part is about how these files got there), read the numbers into arrays and 
use these arrays to draw a plot. Let's use `pip` to install this example package and run it:

```commandline
python3 -m pip install --index-url https://central.artipie.com/olenagerasimova/pypi/ pypiexample
python3 -m pypiexample
``` 

I hope that you see a polar plot with three curves, visualisation of our data files. 

To publish package to the Artipie Central repository build it with `sdist` and use `twine` for upload:

```commandline
python setup.py sdist bdist_wheel
twine upload --repository-url https://central.artipie.com/olenagerasimova/pypi -u olenagerasimova -p *** dist/*
```

I've set up [GitHub action](https://github.com/artipie/pypi-example/runs/1449528914?check_suite_focus=true) 
to upload the example to Artipie Central on release, check the script 
[here](https://github.com/artipie/pypi-example/blob/master/.github/workflows/python-publish.yml).

To sum up, in this chapter we set up PyPi repository in Artipie Central, created sample Python 
project, published and installed it. Now we'll move on to the binary storage and 
I'll show where data files for the example are stored.

## Binary Storage

Artipie can be used as a [storage for any files](https://github.com/artipie/artipie/tree/master/examples/binary), 
this repository is used to store experimental data which are visualised by the Python example. I've created 
binary `data` repository on Central, exact configuration is the following:
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

As in the previous example I've allowed download operation to anyone. Data files are three text 
files with some numbers, here is how the first one looks like:
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
httpie -a olenagerasimova:*** PUT https://central.artipie.com/olenagerasimova/data/y2.dat @data/y2.dat
httpie -a olenagerasimova:*** PUT https://central.artipie.com/olenagerasimova/data/y3.dat @data/y3.dat
```

To download the files use `GET` request

```commandline
httpie -a https://central.artipie.com/olenagerasimova/data/y1.dat > ./data/y1.dat
``` 

or simply open links [one](https://central.artipie.com/olenagerasimova/data/y1.dat), 
[two](https://central.artipie.com/olenagerasimova/data/y2.dat) and 
[three](https://central.artipie.com/olenagerasimova/data/y3.dat) in the browser. 
The Python example downloads these files and visualise them on the polar plot.

As this binary repository API is very simple (http `PUT` and `GET` requests), it's easy to write 
a piece of code in any language to upload and downloads necessary files. What is also important, 
authorisation is supported in Artipie, so it's possible to grant rights to upload/download from 
the repository how it suits your case. 