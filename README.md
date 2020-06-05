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
To use an cc-jupyter-service you need to access its webpage. The HTW hosts a CC-Jupyter-Service installation [here](avocado01.f4.htw-berlin.de/ccjupyterservice). You probably need to access it via
VPN.

#### Docker (optional)
CC-Jupyter-Service executes your notebooks using docker. If you have special software requirements, you may need to
[build your own docker image](https://docs.docker.com/engine/reference/commandline/build/).

#### Storage Server (optional)
If you want to use external data in your jupyter notebook you need SSH access on a SSH server, that is accessible inside the HTW Network.

Via VPN you should be able to access it using `ssh myusername@ssh-server-name` in a terminal.

## Login Page
The login page is the first page you see, when accessing CC-Jupyter-Service with your browser. You can access the HTW installation [here](avocado01.f4.htw-berlin.de/ccjupyterservice).

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Login</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css">
    <link rel="stylesheet" href="/ccjupyterservice/static/style.css">
</head>
<body>

<div class="container">
    <h2>Login</h2>
    <form method='Post'>
        
            <div class="col-xs-5">
                <label for="agencyUrl">Agency URL</label>
                <select class="form-control" name="agencyUrl" id="agencyUrl">
                    
                        <option>https://agency.f4.htw-berlin.de/dt</option>
                    
                        <option>https://agency.f4.htw-berlin.de/cctest</option>
                    
                        <option>https://agency.f4.htw-berlin.de/cc</option>
                    
                </select>
            </div>
        
        <div class="form-group">
            <label for="agencyUsername">Agency-Username</label>
            <input class="form-control" placeholder="Agency-Username" name="agencyUsername" id="agencyUsername" required>
        </div>
        <div>
            <label for="agencyPassword">Agency-Password</label>
            <input class="form-control" placeholder="Agency-Password" type="password" name="agencyPassword" id="agencyPassword" required>
        </div>
        <br>
        <input type="submit" class="btn btn-primary" value="Login">
    </form>
</div>

</body>
</html>
```
