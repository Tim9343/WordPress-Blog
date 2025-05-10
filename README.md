# WordPress-Blog
Guide to create a WordPress Blog using AWS as IaaS

This GitHub repository contains a step by step guide on how to create a WordPress blog using AWS EC2 to create the virtual machine running Ubuntu Server, AWS EBS for storage and AWS Route 53 for domain name and DNS services. After configuring the AWS services, the guide then shows how to install WordPress and the necessary MySQL (MariaDB) database as well as how to create a blog page in WordPress and customising the WordPress theme.

</br>

To deploy WordPress using AWS, this approach uses the LAMP stack approach. This stands for the Linux operating system, the Apache webserver, MySQL as the database and the PHP language which is used by WordPress.

</br>

The documentation includes the following steps:

1. Launching an instance using Amazon EC2 to deploy a virtual machine using Ubuntu Server as the operating system
2. Installing the Apache webserver
3. Allocating an elastic IP address
4. Testing the assignment of the elastic IP address
5. Buying a domain name from Amazon Route 53
6. Mapping the domain name to the elastic IP address using an A record
7. Installing an SSL certificate for a secure HTTPS website
8. Installing an configuring the MySQL database (MariaDB)
9. Installing PHP
10. Downloading and configuring WordPress to be able to login to the WordPress admin console