# Udacity-Linux-Server-Configuration-Project

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
</ul>
<p>--Above step will log you in as the root user. We will want to create at least one new user named <b>grader</b>. See below--
<pre>
<code>sudo adduser grader</code>
</pre>
<ul>
<li><p>Create password for user <b>grader</b> This other information is not needed to create user.</p></li>
<li><p>As <b>root</b> user give user <b>grader</b> sudo permission </li>
</ul>
<pre><code>visudo</code></pre>



<h3>SSH Key Authentication</h3>
<ul>
<li><p>From terminal on local machine type:</p></li>
</ul>
<pre>
<code>ssh-keygen</code>
</pre>
<ul>
<li><p>This key should be stored in the following directory <code>Users/ragan/.ssh/authorized_keys</code> on your local machine</p></li>
<li><p>We need to copy the private key from the <b>local machine</b> to your user <b>grader</b> on the digital ocean server by running <code>ssh-copy-id grader@<your_public_ip_digital_ocean></code></p></li>
<li><p>You can now log in as the user <b>grader</b> from your local machine</p></li>
</ul>
<pre>
<code>ssh grader@(your_public_ip_digital_ocean)</code>
</pre>




<h3>Update & Upgrade All Packages</h3>
<ul>
<li><p>As user <b>grader</b> run the following commands</p></li>
</ul>
<p><code>sudo apt-get update</code></p>

<p><code>sudo apt-get upgrade</code></p>





<h3>Changing SSH Port To 2200</h3>
<ul>
<li><p>Edit the sshd_config file</p></li>
</ul>
<pre>
<code>sudo nano /etc/ssh/sshd_config</code>
</pre>
<ul>
<li><p>Change <b>#Port 22</b> to <b>Port 2200</b></p></li>
</ul>





<h3>Securing Server & Configuring Firewall</h3>
<ul>
<li><p>Log in as the user <b>grader</b></p></li></ul>
<p>Perform the steps below in order</p>

<code>sudo ufw app list</code><p>Lists out profiles to further explore their profile definitions</p>
<code>sudo ufw allow OpenSSH</code><p> Allows open SSH connection</p>
<code>sudo ufw allow 2200</code><p> Allows connection to port 2200</p>
<code>sudo ufw allow 2200/tcp</code><p> Allows <a href="https://stackoverflow.com/questions/8156254/tcp-vs-udp-what-is-a-tcp-connection"><b>Transmission Control Protocol</b></a> on port 2200</p>
<code>sudo ufw allow 80/tcp</code><p> Allows <b>http</b> connection on port 80</p>
<code>sudo ufw allow 123/udp</code><p> Allows <a href="https://www.auditmypc.com/udp-port-123.asp"><b>Network time protocol</b></a> on port 123</p>
<code>sudo ufw enable</code><p> Enables firewall! Make sure your settings are correct first!</p>



<h3>Deploying Application</h3>
<p>........... </p>
<pre>
<code>.........</code>
</pre>


<h3>Setting Up PostgreSQL Database</h3>
<p>........... </p>
<pre>
<code>.........</code>
</pre>


<h3>References</h3>
