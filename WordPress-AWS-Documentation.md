**ICT171 – Assignment 2: Documentation of WordPress as IaaS**
<p>
Tim Fausten

Student ID: 34492493

AWS public DNS: http://ec2-13-238-207-70.ap-southeast-2.compute.amazonaws.com/

Public / elastic IP address: 13.238.207.70

Domain name: www.networking-blog.com 
</p>

</br>


**1. Log-in to AWS EC2 and Launch an instance**
<p>
•	Log-in with your credentials here: http://aws.amazon.com/ec2/

•	Click on “Launch Instance”.

•	Give the new instance a name (“WordPress”).

•	Choose Ubuntu Server 24.04 LTS as Amazon Machine Image.

•	Choose the t2.micro as Instance Type.

•	For the Key Pair, click “create new key pair” for the login and enter a name (“WordPress-key”). Leave the key-pair type as RSA and the file format as .pem.

•	The key will then be downloaded and saved in the Downloads folder.

•	Click on “Edit” for the network settings to create a new security group. Call it “WordPress-SecurityGroup” and enable SSH, HTTP and HTTPS for the webserver.

•	Leave the 30GB of storage under “Add Storage”.

•	Review the summary and click on the orange “Launch Instance” button.

•	You should then see a green success message.


You can then connect to your instance using SSH.

•	Click on “Connect to instance” and choose “SSH Client”.

•	Open your terminal

•	Enter the command to change the permissions of the key file.

•	Enter the command to remotely access the WordPress instance via SSH and accept the fingerprint.
</p>
</br>



**2. Install the Apache webserver**
<p>
•	Before installing Apache, update the apt repository by typing the following command into the terminal:
```markdown
sudo apt update
```
•	Install the Apache webserver using the following command:
```markdown
sudo apt install apache2
```
</p>
</br>

**3. Ensure that the IP address is static**
<p>
•	Navigate back to your Amazon EC2 Dashboard and scroll down until you see “Elastic IPs” under the Network & Security heading on the left side and click on it.

•	Click on “Allocate Elastic IP addresses” and keep the defaults (Amazon’s pool of IPv4 addresses and ap-southeast-2 as network border group) and click on “allocate”.

•	Click on the allocated IPv4 address and then choose “Associate Elastic IP address”.

•	Choose the WordPress instance and the allocated private IPv4 address to associate the elastic IPv4 address with.
</p>
</br>
 


**4. Test if the Apache installation and assignment of public IP address work**
<p>
To test if Apache has been installed successfully and the elastic IPv4 address has been allocated, find out the public IPv4 DNS of the WordPress instance from the AWS EC2 instance details.

When you copy the static public IPv4 address and the public IPv4 DNS address into a web browser, it should show the Apache Default page.
</p> 
</br>


**5. Buy a domain name from Amazon Route 53**
<p>
•	In the AWS Dashboard search tool, search for Route 53 and click “Get started” to register a domain.

•	Follow the steps in AWS to check if the domain name is available, enter your personal details, agree to Terms and Conditions and make the payment.
</p>
</br>
 


**6. Map the domain name to the IP address**
<p>
•	In Amazon Route 53 got to “Hosted Zones”, click on the domain name and then “Create Record”.

•	Then create an A record for the domain and map it to the static public IP address created earlier.

•	To test if the domain name has been mapped, enter the URL into a web browser. It should display the default web page again.
</p>
</br>



**7. Install an SSL certificate from Let’s Encrypt using Certbot**
<p>
•	Connect to the EC2 instance via SSH

•	Install additional snapd repositories by using these commands:
```markdown
sudo snap install core
sudo snap refresh core
```
•	If the Certbot package is already installed, remove it by using this command:
```markdown
sudo apt-get remove certbot
```
•	Install Certbot using this command:
```markdown
sudo snap install --classic certbot
```
•	To make sure that the certbot command can be run, enter the following command:
```markdown
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
•	Run the following command to get a certificate, install it and to turn on HTTPS access:
```markdown
sudo certbot --apache
```

•	Follow the prompts to accept the license and enter the domain name (www.networking-blog.com, networking-blog.com)

•	You should now see a success message

•	To check whether the SSL certificate has been successfully installed, navigate to the website and check if it displays HTTPS in the URL and the lock symbol



Source for installing the SSL certificate: Certbot, certbot.eff.org, https://certbot.eff.org/instructions?ws=apache&os=snap&tab=standard
</p>
</br>