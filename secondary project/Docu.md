# WordPress Installation Documentation


## Step 1:
1. [Download Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
2. Flash SD-kard with etcher
3. Install on Rpi

## Step 2:
1. [Install Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and connect the raspberry pi via IP.

## Step 3:
1. Install apache2
   ```
   sudo apt-get install apache2 -y
   ```

## Step 4:
1. Install Mysql
   ```
   sudo apt-get install mysql-server mysql-client -y
   sudo mysql_secure_installation
   ```

## Step 5:
1. PHP installation
```
sudo apt-get install php php-mysql -y
```
2. Testify if the installation is successful
```
    sudo nano var/  <?php
     phpinfo();
     ?>www/html/phpinfo.php
```
    Then enter

3. Save file Strg+O Enter and close Strg+X Enter

## Step 6:
1. Install phpMyAdmin
```
    sudo apt-get install phpmyadmin -y
```
     Then choose apache2 and press space. Next question answer with yes.
2. Then enter code to get into config
```
     sudo dpkg-reconfigure phpmyadmin
```
After that you have to answer with yes.
First choose the connection via TCP/IP and then take localhost after that enter the                     port or let it empty. You can enter any name you want. Then anter the MySSQL username for phpmyadmin.Next two steps you will set password after your preferences. Afterwards you will set up a username and then you wil have to
choose apache2. It will end up with a error massage and you will have to repeat question skip.

## Step 7:
1. FileZilla installation
```
    sudo apt-get install proftpd -y
    sudo nano /etc/proftpd/proftpd.conf
```
    At the end of the apperaing code you have to add another code
```
    DefaultRoot ~
    AuthOrder mod_auth_file.c
    mod_auth_unix.c
    AuthUserFile /etc/proftpd/ftpd.passwd
    AuthPAM off
    RequireValidShell off
```
    Save with Strg+O and close with Strg+X

## Step 8:
1. Install WordPress

# HomeAssistant Installation

## Step 1:
1. Install phyton3
```
    sudo apt-get install python3 python3-venv python3-pip
```
     Then add an account for home assistant
     ```
    sudo useradd -rm homeassistant -G dialout,gpio
    ```
    Next you create a directory for the installation of Homeassistant and change the owner to the homeassistant account
    ```
    cd /srv
    sudo mkdir homeassistant
    sudo chown homeassistant:homeassistant homeassistant
    ```
    Then you will create and change to a virtual enviroment
    ```
     sudo -u homeassitant -H -s
    cd /srv/homeassistant
    phyton3 -m venv .
   source bin/activate
   ```
    after that when you have ben activated you will have to install required phyton package
    ```
   python3 -m pip install wheel
   ```
  Next you will install the homeassistant
  ```
  pip3 install homeassistant
  ```
Now you can start HASS with the following command
`hass`
