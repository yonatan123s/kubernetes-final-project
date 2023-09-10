1) 
// change the replicas to 5 in the yaml and create it

apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: webapp
  name: webapp
spec:
  replicas: 5
  selector:
    matchLabels:
      app: webapp
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: webapp
    spec:
      containers:
      - image: nginx
        name: nginx
        resources: {}
status: {}

kubectl create -f webapp.yaml



2) kubectl rollout status deploy webapp

3) kubectl get rs -l app=webapp

4)kubectl get rs -l app=webapp -o yaml

kubectl get po -l app=webapp -o yaml

5) kubectl delete deploy webapp

kubectl get po -l app=webapp -w

6) kubectl create deploy webapp --image=nginx:1.17.1 --dry-run -o yaml > webapp.yaml

// add the port section and create the deployment

apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: webapp
  name: webapp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: webapp
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: webapp
    spec:
      containers:
      - image: nginx:1.17.1
        name: nginx
        ports:
        - containerPort: 80
        resources: {}
status: {}

kubectl create -f webapp.yaml

// verify
kubectl describe deploy webapp | grep Image

7) kubectl set image deploy/webapp nginx=nginx:1.17.4

kubectl describe deploy webapp | grep Image

8) kubectl rollout history deploy webapp

kubectl get deploy webapp --show-labels
kubectl get rs -l app=webapp
kubectl get po -l app=webapp

9) kubectl rollout undo deploy webapp

kubectl describe deploy webapp | grep Image

10) kubectl set image deploy/webapp nginx=nginx:1.100

kubectl rollout status deploy webapp (still pending state)

kubectl get pods (ImagePullErr)

kubectl rollout undo deploy webapp
kubectl rollout status deploy webapp

kubectl get pods

kubectl rollout history deploy webapp --revision=7

kubectl set image deploy/webapp nginx=nginx:latest

kubectl rollout history deploy webapp (No new revision)


11) kubectl autoscale deploy webapp --min=10 --max=20 --cpu-percent=85

kubectl get hpa

kubectl get pod -l app=webapp

12) NO QUESTION

13) kubectl delete deploy webapp

kubectl delete hpa webapp

14) kubectl create job hello-job --image=busybox --dry-run -o yaml -- echo "Hello I am from job" > hello-job.yaml

// edit the yaml file to add completions: 10

apiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: hello-job
spec:
  completions: 10
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
      - command:
        - echo
        - Hello I am from job
        image: busybox
        name: hello-job
        resources: {}
      restartPolicy: Never
status: {}

kubectl create -f hello-job.ya

