# Steps for initial setup on Bastion host for deploying applications on EKS cluster

### Install kubectl CLI tool on EC2:

```
curl -o kubectl https://s3.us-west-2.amazonaws.com/amazon-eks/1.23.7/2022-06-29/bin/linux/amd64/kubectl
```
```
chmod +x ./kubectl
```
```
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```
```
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
```
```
kubectl version --short --client
```

### Install  AWS CLI tool on EC2 :

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
```
unzip awscliv2.zip 
```
```
sudo ./aws/install 
```

### Install  eksctl CLI tool on EC2 :

for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`

```
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH
```
```
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
```
```
tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz
```
```
sudo mv /tmp/eksctl /usr/local/bin
```

### Configure AWS Credentials using aws configure command :

```
i)   aws configure
```
```
ii)  AWS Access Key ID [None]: XXXXXXXXXXXXXXXXXXXXXX
```
```
iii) AWS Secret Access Key [None]: XXXXXXXXXXXXXXXXXXXXXX
```
```
iv)  Default region name [None]: region-code
```
```
v)   Default output format [None]:
```

### Update the cluster information in kubeconfig file on EC2:

```
aws eks update-kubeconfig --name cluster-name  --region region-code
```

### To check the list of configured kubernetes clusters run the below command:

```
aws eks list-clusters
```
