# CREER KEY PAIR
aws ec2 create-key-pair --region us-west-2 --key-name devsecops-project --query "KeyMaterial" --output text > devsecops-project.pem

# CHMOD 400 SUR LA KEY PAIR
ex : /home/devsecops-project/jenkins-server-terraform/devsecops-project.pem

# SE CONNECTER EN SSH SUR LE MACHINE JENKINS
aws configure

# INTERFACE GRAPHIUE JENKNS (INSTALLER PLUGING)
aws credential
Pipeline AWS Steps
Docker
NodeJS
SOnarQube Scanner
OWASP
Eclipse Temurin

# SE CONNECTER A SONARCUBE
IP-Publique:9000

# CREER 2 PROJETS un Backend et un Frontend
Creat Project > Locally > Generate > Continue > Other > Linux
Copier le code et remplacer dans jenkisfile-backend && jenkisfile-fronted

# CREER UN TOKEN
Administration > Security > User
Generer la Key et copier dans notes.txt

# CREER UN WEBHOOK
Cofiguration > Webhook > Create Webhook
http://IP-PUBLIQUE -JENKINS:8080/sonarqube-webhook/

# CREER UN REPOSITORY AVEC ECR
- 1 x frontend
- 1 x backend 
cliquer sur afficher les commandes Push 
Copier le commande aws ecr get-login-password --region us-west-2 | docker login --username AWS... sur la serveur JENKINS

Remplacer url de image dans Kubernetes > Backend > deployment.yaml par URL du bakkend ECR

# CREER CREDENTIALS SUR LE SERVEUR JENKINS
- aws
- github
- sonar token 
- ecr rpo frontend et backend
- account id

# CONFIGURER MANAGE TOOL (Install auto)
- JDK
- GIT
- SONNARQUEB Scanner
- NOdeJS
- Dependensy-Check
- DOCKER

# Copier l'adresee IP de SonarCube dans administrer jenkins > System

# CREER AWS CLUSTER (dans kubernetes-manifest)
eksctl create cluster -f eks-cluster.yaml

# Télécharger les policy pour le LB
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json

# CREER IAM Policy
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json

# CREER OIDC Provider
eksctl utils associate-iam-oidc-provider --region=us-west-2 --cluster=three-tier-k8s-eks-cluster --approve