Cloudnative security: EKS deployment with Nginx and Let's Encrypt
-----------------------------------------------------------------

Production level deployment project involving setting up SSL/TLS certificates from Let's Encrypt with NGINX ingress controller on AWS EKS cluster

Prequisites :
1. AWS Account with EKS access
2. AWS CLI : https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
3. Helm : https://helm.sh/docs/intro/install/
4. Kubectl : https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
5. Eksctl : https://eksctl.io/installation/




 eksctl create cluster --name eks-ssl --region us-east-1 --nodegroup-name eks-ssl-nodegroup --node-type t3.small --managed --nodes 2

aws eks update-kubeconfig --region us-east-1 --name ssl-cluster

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress-nginx --create-namespace \
 --set-string controller.service.annotations."service\.beta\.kubernetes\.io/aws-load-balancer-type"="nlb"



kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.3/cert-manager.crds.yaml

 kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.3/cert-manager.yaml
