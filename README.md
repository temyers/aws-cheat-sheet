# AWS CLI Cheat Sheet

## EC2

### Create a new Elastic IP Address
    
    aws ec2 allocate-address --domain vpc
    
## VPC

### Find the VPC ID for a given name
    aws ec2 describe-vpcs --filters "Name=tag:Name,Values=MY-NAME-HERE" --query "Vpcs[0].VpcId"
    
`"vpc-f6372692"`

### Find the public DNS name for an ELB

    aws elb describe-load-balancers --query "LoadBalancerDescriptions[?VPCId == 'vpc-f6372692'].{"VPCId":VPCId,"DNSName":DNSName,"Scheme":Scheme} | [?Scheme == 'internet-facing'] | [0].DNSName"
"MY-ELB-DNS.us-east-1.elb.amazonaws.com"