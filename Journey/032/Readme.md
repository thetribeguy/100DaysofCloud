# New post title here

Install AWS CLI - https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html In IAM, create an access key in IAM credentials. In the terminal, configure credentials by entering the following commands: aws configure Fill in the fields.

Step 3
Install kubectl - https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html and follow the steps to complete installation Ensure that the kubectl exe is in the usr/local/bin folder.

Check status of cluster with the following command: aws eks --region us-east-1 describe-cluster --name Kube01 --query cluster.status If it is not connecting to the endpoint , enter this command: "aws configure set region us-west-1 --profile default" to set the region parameters

Update Kubeconfig with the following command: aws eks --region us-east-1 update-kubeconfig --name Kube01 Ensure that kubectl can is operating properly by the following command: "kubectl get svc"

Create a YAML file for the base EKS cluster to be deploted.
