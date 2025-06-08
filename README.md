### Access-S3-from-private-EC2-instance-using-VPC-endpoint-
# Purpose of the Hands on
Access to the S3 backet from Private instance in VPC through Gateway endpoint without using external network.

### Methods

1 Create VPC with IP add 192.168.0.0/26
2 Create Internet Gateway then attached to our VPC
3 Create Public Instance with IP add 192.168.0.1/27 then enable auto-assign public IPV4 address in Public subnet
4 Create Private Instance with IP add 192.168.0.32/27 
5 Create Route table one for public Subnet and target (Internet gateway in the Route to allow internet traffic to the VPC)the second for private subnet
6 
