#  Create Kubernetes cluster in aws ec2 using kops 

## 1) Create  a new Ubuntu 20 ec2 instance 

 We need this instance to configure aws cli and kops and create cluster from this machine .

## 2) Install aws cli

logon to the ec2 instance and install aws cli
 
```
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

sudo apt install unzip

sudo unzip awscliv2.zip

sudo ./aws/install

aws --version

```

## 3) Install kubectl 
Kubectl is the tool through which we will call kubernetes api's

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
 chmod +x ./kubectl
 sudo mv ./kubectl /usr/local/bin/kubectl
```

## 4) Create an IAM role with the following full access  

See the screen shot below 

<img src="roles.png"/>

## 5) Attach IAM role to ubuntu server
      
	   Select the ec2 instance and go to actions -> instance settings -> Modify IAM role
	   
	   <img src="attachrole.png"/>
	   
	   In this screen choose the role what we had created in step 4 . I had created kss-role and i attached it with this ec2 machine 
     
	 <img src="chooserole.png"/>

## 6) configure aws 
  
  ```
  aws configure
  ```
  Do not provide 
  

