# Installation Guide
**Nginx** is a high performance web server as a reverse proxy. Following steps guide you to setup configuration as Reverse Proxy with SSL on Ubuntu Server.

1. Connect to remote machine where Nginx is installed. SSH as `root` into your machine by following commands.

        $ SSH root@<Your-Remote-IP-Address>  

2. Continue by running update and installation **Nginx**.

        $ sudo apt-get update
        $ sudo apt-get install nginx
        
    > **NOTE** <br/> Following commands are used to change status of **Nginx** service on server. Then, you can test **Nginx** is running by visiting `Server IP Address` in your browser. <br/> `sudo systemctl stop nginx`<br/> `sudo systemctl start nginx`<br/> `sudo systemctl enable nginx`

3. Unlink default configuration of the Nginx host by following commands.

        $ sudo unlink /etc/nginx/sites-enabled/default

4. Go to `sites-enabled` directory which we will create configuration file by following commands.

        $ sudo cd etc/nginx/sites-available

5. Create a configuration file and open with nano editor. Then, copy **reverse-proxy.conf** file contents into created file.

        $ sudo nano reverse-proxy.conf
        
6. Activate config file that we created by symlink to `sites-enabled` directory by following commands.

        $ sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf

    > **NOTE** <br/> You can test your configuration file by following command;<br/> `sudo nginx -t`

7. Finally restart Nginx service to configure new proxy configuration file.

        $ sudo systemctl restart nginx
