# How to run GOST on Raspberry Pi

Warning: Raspberry Pi support for GOST is in experimental phase! Maybe it works if you are lucky.

## Flash card

For running GOST we need to have a flash card with Docker installed.

One easy option is to use the <a href="https://blog.hypriot.com/">Hypriot</a> images, it comes with Docker tools installed.

Installation instructions:

- For Mac: https://blog.hypriot.com/getting-started-with-docker-and-mac-on-the-raspberry-pi/

- For Windows: https://blog.hypriot.com/getting-started-with-docker-and-windows-on-the-raspberry-pi/

- For Linux: https://blog.hypriot.com/getting-started-with-docker-and-linux-on-the-raspberry-pi/

Use the latest Hypriot image: https://github.com/hypriot/image-builder-rpi/releases/download/v1.5.0/hypriotos-rpi-v1.5.0.img.zip (29.06.2017)

After installation, you should be able to loging on machine 'black-pearl' with 'pirate' as username, password 'hypriot'

```
$ ssh pirate@black-pearl
``
Now update the installation:

```
$ sudo apt-get update
$ sudo apt-get upgrade docker-hypriot docker-compose
```

## Install GOST

Execute the following commands to install GOST on the Raspberry Pi.

Note: downloading new images can take some time... So grab a coffee and relax while GOST is installing... 

```
$ wget https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose-rpi.yml
$ sudo docker-compose -f docker-compose-rpi.yml up
```

## Check installation

- Dashboard: In browser go to http://black-pearl:8080

- Create a thing in dashboard

If the dashboard is working, you can continue with the <a href="https://github.com/gost/workshops/blob/master/2_configuration.md">Workshop exercises</a> to configure GOST. Make sure to replace 'localhost' with 'black-pearl' in the exercises. 
