# Welcome to the CC-Jupyter-Service documentation

## Introduction
This guide shows you how to use **CC-Jupyter-Service** to execute jupyter notebooks. It will show you how to use external data in you notebook and how to specify Hardware and Software requirements.

It is written for students or employees of the HTW Berlin.

## Prerequisites
#### Jupyter Notebook
CC-Jupyter-Service enables you to execute jupyter notebooks. Therefor it is required to **write and save a jupyter notebook** on your machine (or at least you need access to a notebook file).

#### CC-Agency-Account
CC-Jupyter-Service uses *CC-Agency* for authorization and execution of the notebooks. Therefor it is required to have access to a CC-Agency installation. You will need the **URL** of the agency and
a valid **Username** and **Password** combination.

You can test whether you have access to an agency by accessing "*agencyUrl*/nodes" with your browser. You will be asked for username/password.

If you cannot access the agency it may be required to access it via VPN (See [this](https://anleitungen.rz.htw-berlin.de/de/vpn/) guide on how to setup VPN at the HTW Berlin).

#### Access to an CC-Jupyter-Service installation
To use an cc-jupyter-service you need to access its webpage. The HTW hosts a CC-Jupyter-Service installation [here](https://avocado01.f4.htw-berlin.de/ccjupyterservice). You probably need to access it via
VPN.

#### Docker (optional)
CC-Jupyter-Service executes your notebooks using docker. If you have special software requirements, you may need to
[build your own docker image](https://docs.docker.com/engine/reference/commandline/build/).

#### Storage Server (optional)
If you want to use external data in your jupyter notebook you need SSH access on a SSH server, that is accessible inside the HTW Network.

Via VPN you should be able to access it using `ssh myusername@ssh-server-name` in a terminal.

## Login Page
The login page is the first page you see, when accessing CC-Jupyter-Service with your browser. You can access the HTW installation [here](https://avocado01.f4.htw-berlin.de/ccjupyterservice).

![Login Page](https://media.githubusercontent.com/media/curious-containers/cc-jupyter-service.github.io/master/images/login.png)

Here you need the agency URL and your username/password combination of your agency account.

If you are a student at the HTW you should probably select `https://agency.f4.htw-berlin.de/dt`.

## Execution Page
If you have logged in successfully you see the execution page.

![Execution Page](https://media.githubusercontent.com/media/curious-containers/cc-jupyter-service.github.io/master/images/execution.png)

#### Jupyter Notebook
As stated previously CC-Jupyter-Service executes a jupyter notebook. In the first section of the execution page you can drag and drop your jupyter notebook file.

![Jupyter Notebook](https://media.githubusercontent.com/media/curious-containers/cc-jupyter-service.github.io/master/images/notebook.png)

Afterwards you can see the notebook file. To execute a different notebook remove the notebook by clicking the X-Button next to the notebook name.

#### Dependencies
CC-Jupyter-Service executes your notebook inside a docker container. If you don't need extra software you can simply select "Base Image". There is also a predefined "Tensorflow Image".

There are two options in case you want python packages that are not installed in the predefined images.

**Option 1:** You can use `!pip install <package>` inside your notebook to install a python package while executing the notebook. This is relatively easy to implement.
The downside is that the python package is installed every time you execute the notebook. Also this does not work, if you want to install software not based on python.

**Option 2:** The more sophisticated approach is to build your own docker image. Afterwards you can choose this image by selecting "Custom Docker Image" and specifying your image tag.
To make a docker image work under CC-Jupyter-Service there are some requirements. Read [TODO](#) for more information on how to build your own docker image for CC-Jupyter-Service.

#### GPUs
For machine learning applications or image processing it is sometimes useful to use GPU-acceleration. For this purpose you can require one or more GPUs by clicking on the Plus-Button under GPUs.
A new GPU-Entry should appear where you can select the amount of VRAM of this GPU. You can require as much GPUs as you like but if the cluster does not have the possibility to fullfill these
requirements the execution of the notebook will fail.

When using dt-agency you can select a maximum of two GPUs otherwise the execution will fail.

#### External Data
