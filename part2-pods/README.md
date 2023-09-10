1) kubectl get pods --show-labels
   
2) kubectl run nginx-dev1 --image=nginx --restart=Never --labels=env=dev
kubectl run nginx-dev2 --image=nginx --restart=Never --labels=env=dev
kubectl run nginx-dev3 --image=nginx --restart=Never --labels=env=dev
kubectl run nginx-prod1 --image=nginx --restart=Never --labels=env=prod
kubectl run nginx-prod2 --image=nginx --restart=Never --labels=env=prod

3) kubectl get pods --show-labels

4) kubectl get pods -l env=dev 

5) kubectl get pods -l env=dev --show-labels

6) kubectl get pods -l env=prod

7) kubectl get pods -l env=prod --show-labels

8) kubectl get pods -L env

9) kubectl get pods -l 'env in (dev,prod)'

10) kubectl get pods -l 'env in (dev,prod)' --show-labels

11) kubectl label pod/nginx-dev3 env=uat --overwrite

kubectl get pods --show-labels

12) kubectl label pod nginx-dev{1..3} env-
kubectl label pod nginx-prod{1..2} env-

kubectl get po --show-labels

13) kubectl label pod nginx-dev{1..3} app=nginx
kubectl label pod nginx-prod{1..2} app=nginx

kubectl get po --show-labels

14) kubectl get nodes --show-labels

15) kubectl label node nodeName=nginxnode

16) kubectl run nginx --image=nginx --restart=Never --dry-run -o yaml &gt; pod.yaml



apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: nginx
spec:
  nodeSelector:
    nodeName: nginxnode
  containers:
  - image: nginx
    name: nginx
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}

kubectl create -f pod.yaml


17) kubectl describe po nginx | grep Node-Selectors

18) kubectl describe po nginx | grep Labels
