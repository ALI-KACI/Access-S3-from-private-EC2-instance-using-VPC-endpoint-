### Access-S3-from-private-EC2-instance-using-VPC-endpoint-
# Purpose of the Hands on
Access to the S3 backet from Private instance in VPC through Gateway endpoint without using external network.

### Methods

1. Create VPC with IP add `192.168.0.0/26`
2. Create Internet Gateway then attached to our VPC
3. Create Public Subnet with IP add `192.168.0.1/27` with:
   - auto-assign public IPV4 address
4. Create Private Subnet with IP add `192.168.0.32/27` 
5. Create Route tables:
   - Public:  Route to Internet gateway
   - Private: Default route
6. Create security groups:
   - Bastion: Allow SSH,HTTP,HTTPs
   - private: Allow SSH from Bastion 
7. Create VPC Endpoint to access in S3 backet 
8. SSH into private instance through Bastion host
   ```bash
     # Connect to Bastion
        aws ec2-instance-connect ssh --instance-id i-bastion...
   
     # Transfer key
       vi WhizKey.pem
       chmod 400 WhizKey.pem
   
     # SSH to Private
       ssh -i "WhizKey.pem" ec2-user@192.168.0.60
    
     # Configure AWS CLI
       aws configure
     # Enter AWS credentials and region

     # Test S3 access
       aws s3 ls
    

