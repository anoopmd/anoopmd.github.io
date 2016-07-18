---
layout: post
title: Setting Basic HTTP Authentication on Nginx
---

I am using Ubuntu 14.04. The default public directory is /usr/share/nginx/html

### Pre-requisites
* Nginx

#### Step 1: Installing Apache Tools <br>
`sudo apt-get install apache2-utils`

#### Step 2: Setting Up HTTP Basic Authentication Credentials <br>
That password and the associated username will be stored in a file that you specify. The password will be encrypted and the name of the file can be anything you like. Here, we use the file `/etc/nginx/.htpasswd nginx

`sudo htpasswd -c /etc/nginx/.htpasswd nginx`

You can check the contents of the newly created file to see the username and hashed password. <br>
` cat /etc/nginx/.htpasswd`

#### Step 3: Updating the Nginx Configuration <br>
HTTP basic authentication is made possible by the auth_basic and auth_basic_user_file directives. The value of auth_basic is any string, and will be displayed at the authentication prompt; the value of auth_basic_user_file is the path to the password file that was created in Step 2 <br>

Open the nginx config file <br>
`sudo vim /etc/nginx/sites-available/default`

Under the location section, add both directives:
<pre>
location / {
        # First attempt to serve request as file, then
        # as directory, then fall back to displaying a 404.
        try_files $uri $uri/ =404;
        # Uncomment to enable naxsi on this location
        # include /etc/nginx/naxsi.rules
        auth_basic "Private Property";
        auth_basic_user_file /etc/nginx/.htpasswd;
}
</pre>

#### Step 4: Testing the setup <br>
To apply the changes, first reload Nginx. <br>

`sudo service nginx reload`

Now try accessing the website you just secured by going to http://your_server_ip/ in your favorite browser. You should be presented with an authentication window (which says "Private Property", the string we set for auth_basic), and you will not be able to access the website until you enter the correct credentials.


#### References
[Do Article](https://www.digitalocean.com/community/tutorials/how-to-set-up-basic-http-authentication-with-nginx-on-ubuntu-14-04)