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

## 5) Apply the role to ec2 instance 

	   Select the ec2 instance and go to actions , instance settings , Modify IAM role
	   
	   <img src="attachrole.png"/>
	   
	   In this screen choose the role what we had created in step 4 . I had created ks8-role and i attached it with this ec2 machine 
     
	 <img src="chooserole.png"/>

## 6) configure aws 
  
  ```
  
  aws configure
  
  ```
  Do not provide accesskey, secret key , default region enter the region in which we created the ec2 instance 
  I am using us-east-2 
  Do not enter anything in default output format 
  
## 7) Install kops on ubuntu instance

```

curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
 chmod +x kops-linux-amd64
 sudo mv kops-linux-amd64 /usr/local/bin/kops

```

## 8) Create a Route53 private hosted zone (you can create Public hosted zone if you have a domain)

    Go to Route53 and create a private zone and attach the vpc which is created for the zone(us-east-2)


## 9) Create S3 bucket 

```

aws s3 mb s3://dev.k8s.mindbridges.in

export KOPS_STATE_STORE=s3://dev.k8s.mindbridges.in

```

## 10) Create sshkeys before creating cluster

ssh-keygen

will ask for file, passphrase do not enter any info .. just click enter button 


## 11) Create kubernetes cluster definitions on S3 bucket

```

kops create cluster --cloud=aws --zones=us-east-2b --name=dev.k8s.mindbridges.in --dns-zone=mindbridges.in --dns private

```

## 12) Create Kubernetes Cluster 

```

kops update cluster dev.k8s.mindbridges.in --yes --admin


```

## 13) Validate the cluster 


```

kops validate cluster

```

## 14) List Nodes 

```

kubectl get nodes

```

