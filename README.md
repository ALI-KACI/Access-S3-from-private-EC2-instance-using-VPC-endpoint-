### Access-S3-from-private-EC2-instance-using-VPC-endpoint-
# Purpose of the Hands on
Access to the S3 backet from Private instance in VPC through Gateway endpoint without using external network.

### Methods

1 Create VPC with IP add 192.168.0.0/26<br/> 
2 Create Internet Gateway then attached to our VPC
3 Create Public Instance with IP add 192.168.0.1/27 then enable auto-assign public IPV4 address in Public subnet
4 Create Private Instance with IP add 192.168.0.32/27 
5 Create Route table one for public Subnet add a target (Internet gateway in the Route to allow internet traffic to the VPC)the second for private subnet
6 Create two security group one will be used for bastion host with SSH,HTTP,HTTPs for inbound rules, the second one for private instance having access to VPC Endpoint for S3 with SSH inbound rule and bastion host as a source.
7 Create VPC Endpoint to access in S3 backet.
8 SSH into private instance through Bastion host
    First connect to bastion host using EC2 instance connect
    Second copy the content of the key pair (WhizKey.pem) into it by using this command: vi Whizkey.pem
    Change the permission of the key file by using this command: chmod 400 Whizkey.pem
    Login to Private subnet by using: ssh -i WhizKey.pem ec2-user@Private IP add for Private instance.
    List all the S3 bucket and it is objects by using these command: aws configure
                                                                     add the key ID
                                                                     add Secret access Key
                                                                     Default region name
                                                                     Enter
                                                                     aws s3 ls

    
