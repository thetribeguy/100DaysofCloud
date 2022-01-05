## Set up EKS Cluster and Configurations

![image](https://user-images.githubusercontent.com/82836111/148139447-41959e96-8a6b-4359-a34a-b617bf7e7880.png)

Amazon EKS is a managed service that is used to run Kubernetes on AWS. Using EKS users doesn’t have to maintain a Kubernetes control plan on their own. It is used to automate the deployment, scaling, and maintaining the containerized application. It works with most of the operating systems.

EKS is integrated with various AWS services:

ECR (Elastic Container Registry) for container images.
Elastic Load Balancer for distributing traffic.
IAM for providing authentication and authorization.
VPC (Virtual Private Cloud) for isolating resources.

### Step 1 

Navigate to EKS and click add cluster at the right.

Fill in the fields with the default values. For the role, create or add the AmazonEKSClusterPolicy and select it in the Cluster Service Role box of the confirure cluster page and click next.

On the Specify Networking page, specify your VPC and subnets. 

You can leave the endpoint as public for testing purposes and click next.

Leave configure logging controls as disabled and click next and create.

### Step 2

Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
In IAM, create an access key in IAM credentials.
In the terminal, configure credentials by entering the following commands: aws configure
Fill in the fields.

### Step 3

Install kubectl - https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html and follow the steps to complete installation
Ensure that the kubectl exe is in the usr/local/bin folder.

Check status of cluster with the following command: aws eks --region us-east-1 describe-cluster --name Kube01 --query cluster.status 
If it is not connecting to the endpoint , enter this command: "aws configure set region us-west-1 --profile default" to set the region parameters

Update Kubeconfig with the following command: aws eks --region us-east-1 update-kubeconfig --name Kube01
Ensure that kubectl can is operating properly by the following command: "kubectl get svc"

### Step 4

On the cluster page, select the Compute tab, and then choose Add Node Group.

On the Configure node group page, fill out the parameters accordingly, and then choose Next.

Name – Enter a unique name for your managed node group.
Node IAM role name– Create the node instance role to use with your node group. This EC2 role should contain the following three policies:
AmazonEKSWorkerNodePolicy, AmazonEC2ContainerRegistryReadOnly, AmazonEKS_CNI_Policy.

![image](https://user-images.githubusercontent.com/82836111/148140049-44b958d8-68f8-4e94-8964-b11437e6f153.png)

Create an SSH pair and add the same in the Key pair, proceed to next.



After following all the above image steps, leave the other settings to default and proceed further.



[link](link)
