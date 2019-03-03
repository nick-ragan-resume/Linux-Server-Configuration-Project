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
<p>--Above step will log you in as the root user. We will want to create at least one new user named <b>grader</b>. See below--
<pre>
<code>sudo adduser grader</code>
</pre>
<li><p>Create password for user <b>grader</b> This other information is not needed to create user.</p></li>
  <li><p>As <b>root</b> user give user <b>grader</b> sudo permission <pre><code>visudo</code></pre>
</ul>



<h3>SSH Key Authentication</h3>
<li><p>From terminal on local machine type:</p></li>
<pre>
<code>ssh-keygen</code>
</pre>
<li><p>This key should be stored in the following directory <code>Users/ragan/.ssh/authorized_keys</code> on your local machine</p></li>
<li><p>We need to copy the private key from the <b>local machine</b> to your user <b>grader</b> on the digital ocean server by running <code>ssh-copy-id grader@<your_public_ip_digital_ocean></code></p></li>

<h3>Changing SSH Port To 2200</h3>
<p>........... </p>
<pre>
<code>.........</code>
</pre>


<h3>Securing Server & Configuring Firewall</h3>
<p>........... </p>
<pre>
<code>.........</code>
</pre>


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
