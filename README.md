# Linux-Server-Configuration-Project-Udacity

<h3>Digital Ocean Server Set Up</h3>
<p>Link to digital ocean https://www.digitalocean.com/</p>
<ul>
<li>Create New Droplet</li>
<li>Select the Ubuntu Image</li>
<li>Do Not Set Up SSH Key Here!</li>
<li>Click Create</li>
</ul>


<h3>Logging In & Creating User grader With Sudo Permission</h3>
<p>Click on the newly create droplet</p>
<ul>
<li>Click on the newly create droplet</li>
<li>Click on console</li>
<li>Login to server with username/password sent to your email associated with your digital ocean accout</li>
<p>--Above step will log you in as the root user. We will want to create at least one new user named <b>grader</b>. See below--</p>
<code>sudo adduser grader</code>
</ul>
<ul>
<li><p>Create password for user <b>grader</b> This other information is not needed to create user.</p></li>
<li><p>As <b>root</b> user give user <b>grader</b> sudo permission </li>
<code>visudo</code>
</ul>


<h3>SSH Key Authentication</h3>
<ul>
<li><p>From terminal on local machine type:</p></li>
<code>ssh-keygen</code>
</ul>
<ul>
<li><p>This key should be stored in the following directory <code>Users/ragan/.ssh/authorized_keys</code> on your local machine</p></li>
<li><p>We need to copy the private key from the <b>local machine</b> to your user <b>grader</b> on the digital ocean server by running <code>ssh-copy-id grader@(your_public_ip_digital_ocean)</code></p></li>
<li><p>Set Permissions both .ssh file locations</p></li>
<code>chmod 700 .ssh</code>
<code>chmod 644 .ssh/authorized_keys</code>
<li><p>You can now log in as the user <b>grader</b> from your local machine</p></li>
<code>ssh grader@(your_public_ip_digital_ocean)</code>
</ul>



<h3>Update & Upgrade All Packages</h3>
<ul>
<li><p>As user <b>grader</b> run the following commands</p></li>

<p><code>sudo apt-get update</code></p>

<p><code>sudo apt-get upgrade</code></p>
</ul>


<h3>Changing SSH Port To 2200</h3>
<ul>
<li><p>Edit the sshd_config file</p></li>
<code>sudo nano /etc/ssh/sshd_config</code>
<li><p>Change <b>#Port 22</b> to <b>Port 2200</b></p></li>
</ul>



<h3>Disable Root Login & Password Authentication</h3>
<ul>
<li><p>These settings will be in the sshd_config file also<p></li>
<code>sudo nanno /etc/ssh/sshd_config</code>
<li><p>Find and disable the following lines by setting to no</p></li>
<code>PermitRootLogin no</code>
  </br>
<code>PasswordAuthentication no</code>
</ul>




<h3>Securing Server & Configuring Firewall</h3>
<ul>
<li><p>Log in as the user <b>grader</b></p></li>
<li><p>Perform the steps below</p></li>
<code>sudo ufw app list</code><p> Lists out profiles to further explore their profile definitions</p>
<code>sudo ufw allow OpenSSH</code><p> Allows open SSH connection</p>
<code>sudo ufw allow 2200</code><p> Allows connection to port 2200</p>
<code>sudo ufw allow 2200/tcp</code><p> Allows <a href="https://stackoverflow.com/questions/8156254/tcp-vs-udp-what-is-a-tcp-connection"><b>Transmission Control Protocol</b></a> on port 2200</p>
<code>sudo ufw allow 80/tcp</code><p> Allows <b>http</b> connection on port 80</p>
<code>sudo ufw allow 123/udp</code><p> Allows <a href="https://www.auditmypc.com/udp-port-123.asp"><b>Network time protocol</b></a> on port 123</p>
<code>sudo ufw enable</code><p> Enables firewall! Make sure your settings are correct first!</p>
</ul>


<h3>Deploying Application</h3>
<p>To host our application we will use <b>Virtualenv</b> and <b>Apache2</b></p>
<ul>
<li><p>Installing all packages</p></li>
<code>sudo apt-get install libapache2-mod-wsgi python-dev</code>
<code>sudo apt-get install apache2</code>
<li><p>Once installed, Enable mod_wsgi</p></li>
<code>sudo a2enmod wsgi</code>
<li><p>Now you can start the webserver</p></li>
<code>sudo service apache2 start</code>
<li><p>Now go to the public ip your application is hosted on and you should see an Apache2 Ubuntu Default Page that says It works!</p></li>
<li><p>Create a .wsgi file in the following directory <code>/var/www/catalog</code></p></li>
<p><code>sudo nano catalog.wsgi</code></p>
<pre>
<code>import sys</code>
<code>import logging</code>
<code>logging.basicConfig(stream=sys.stderr)</code>
</br>
<code>from catalog import app as application</code>
<code>application.secret_key = 'supersecretkey'
  </pre>
</ul>

<h3>Install Git To Clone Application</h3>
<ul>
<li><p>You will need to check to see if Git is installed</p></li>
<code>which git</code>
<li><p>If git is not installed run the following command</p></li>
<code>sudo apt-get install git</code>
<li><p>Clone your app in the following directory <code>cd /var/www/catalog</code></p></li>
<li><p>Steps to do this</p></li>
<p><code>cd /var/www</code></p>
<p><code>sudo mkdir catalog</code></p>
<li><p>Give user <b>grader</b> permissions to this directory</p></li>  
<code>sudo chown -R grader:grader catalog</code>
<li><p>Now clone your app from GitHub</p></li>
<code>git clone (clone url link) catalog</code>
<li><p>Your directory should look like this after cloning <code>/var/www/catalog/catalog</code></p></li>  
</ul>


<h3>Install Virtual Environment</h3>

<h3>Setting Up PostgreSQL Database</h3>



<h3>References</h3>
