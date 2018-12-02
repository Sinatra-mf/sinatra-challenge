# sinatra-challenge
https://github.com/Sinatra-mf/sinatra-challenge

# Description:

Provison a new application server using AWS CloudFormation customized template to deploy WordPress application on a Linux image, WordPress is a open-source content management web software based on PHP and MySQL which you can use to create a website or blog.

To properly deploy this package, you are required to have an AWS account to login to AWS console and some knowledge of using AWS CloudFormation tool to create a new Stack.

# Requirements:

AWS account 

CloudFormation Management console

A predefined EC2 KeyPair (to enable SSH access to your EC2 instance)

Base image: Amazon Linux which will be running on EC2 t2.micro (Free tier) and gp2 Volume type

# Solution

Using JSON codes as "configuration-as-code recipes" to integrate better with AWS. This script needs to be run via CloudFormation tool to deploy the application and provides the Website URL.

Example:http://ec2-13-55-40-147.ap-southeast-2.compute.amazonaws.com/wordpress 

Deployment:

1- The script creates a single Amazon Linux EC2 instance with a local MySQL database for storage. 

2- Installing and configure httpd to run a WebServer.

3- Downloading and install open-source WordPress web application from http://wordpress.org.

4- providing the Website URL as an output.

Security:

1- The script creates a security group called "WebServerSecurityGroup" and attach it to the main VPC which running our EC2 instance.

2- It enbales HTTP inbound access via port 80 from any source 0.0.0.0/0.

3- It enables SSH inbound access via port 22 from any source 0.0.0.0/0, this provides a secure and encrypted access to EC2 instance using by SSH key. This option can be restricted to specific IPs during deployment.

4- The outbound traffic is permitted for all protocols, this left open for ease of this project and can be limited based on a request.

5- Script defines several securiy parameters to access the WordPress databse.These includes "DBUser", "DBPassword" and "DBRootPassword".





