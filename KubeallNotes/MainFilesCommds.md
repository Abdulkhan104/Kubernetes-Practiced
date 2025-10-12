#################################  ABHINASH bRO FILE ################################


curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

 sudo mv /tmp/eksctl /usr/local/bin
   eksctl version


eksctl create cluster --name abdul  \
   --region us-east-1 \
   --node-type t2.medium \
   --nodes-min 2 \
   --nodes-max 2 \ 
  


curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl


chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

yum install git -y
yum install docker -y
systemctl start docker 
systemctl status docker

kubectl delete deployment --all
kubectl delete svc --all
kubectl delete hpa --all
kubectl delete pods --all

##day 5

Horizontal Scaling

yum install git -y
kubectl get node
kubectl apply -f .
kubectl get pods 
kubectl top nods
kubectl top pod

kubectl get deployment metrics-server -n kube-system

Clustor Autoscale

kubectl apply -f https://raw.githubusercontent.com/kubernetes/autoscaler/cluster-autoscaler-1.29.0/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml

kubectl -n kube-system get pods -l app=cluster-autoscaler

kubectl -n kube-system edit deployment.apps/cluster-autoscaler

attach in worker node adminacces othwise cant be autoscle

aws eks update-nodegroup-config \
  --cluster-name abdul \                                                    ##########chnge the your cluser name here
  --nodegroup-name ng-4899a1d4 \                                   ##########chnge the your node name here
  --scaling-config minSize=2,maxSize=6,desiredSize=3




