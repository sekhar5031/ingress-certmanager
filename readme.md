Cloudnative security: EKS deployment with Nginx and Let's Encrypt
-----------------------------------------------------------------

Production level deployment project involving setting up SSL/TLS certificates from Let's Encrypt with NGINX ingress controller on AWS EKS cluster

Prequisites :
1. AWS Account with EKS access
2. AWS CLI
3. Helm
4. Kubectl
5. Eksctl


helm upgrade - install ingress-nginx ingress-nginx - repo https://kubernetes.github.io/ingress-nginx - namespace ingress-nginx - create-namespace \
 - set-string controller.service.annotations."service\.beta\.kubernetes\.io/aws-load-balancer-type"="nlb"