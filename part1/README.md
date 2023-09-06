```
Please make sure to write the commands you are writing as a separate document 
and send all of your solutions to a repository that you own.
Please send me the repo - make sure it’s public.
```

# Part 1
1. Deploy a pod named nginx-pod using the `nginx:alpine` image.
Name: nginx-pod-yourname
Image: nginx:alpine

`
kubectl run nginx-pod-yonatan --image=nginx:alpine
`

2. Deploy a messaging pod using the `redis:alpine` image with the labels set to `tier=msg`.
Pod Name: messaging
Image: redis:alpine
Labels: tier=msg

`
kubectl run messaging --image=redis:alpine --labels=tier=msg
`

3. Create a namespace named `apx-x998-yourname`

`
kubectl create namespace apx-x998-yonatan
`

4. Get the list of nodes in JSON format and store it in a file at /tmp/nodes-yourname

`
kubectl get nodes -o json > /tmp/nodes-yonatan.json
`

5. Create a service messaging-service to expose the messaging application within the cluster on port 6379.
        a. Use imperative commands - kubectl
        b. Service: messaging-service
        c. Port: 6379
        d. Type: ClusterIp
        e. Use the right labels
`
kubectl expose pod messaging --port=6379 --name=messaging-service --type=ClusterIp 
`

6. Create a service messaging-service to expose the messaging application within the cluster on port 6379.
        a. Service: messaging-service
        b. Port: 6379
        c. Type: ClusterIp
        d. Use the right labels
`
kubectl ...
`

7. Create a deployment named hr-web-app using the image kodekloud/webapp-color with 2 replicas
        a. Name: hr-web-app
        b. Image: kodekloud/webapp-color
        c. Replicas: 2
`
kubectl run hr-web-app --image kodekloud/webapp-color --replicas=2
`

8. Create a static pod named static-busybox on the master node that uses the busybox image and the command sleep 1000
        a. Name: static-busybox
        b. Image: busybox

`
kubectl ...
`

9. Create a POD in the finance-yourname namespace named temp-bus with the image redis:alpine
        a. Name: temp-bus
        b. Image Name: redis:alpine

`
kubectl run --generator=run-pod/v1 -n finance temp-bus --image redis:alpine
`

10. Create a Persistent Volume with the given specification
        a. Volume Name: pv-analytics
        b. Storage: 100Mi
        c. Access modes: ReadWriteMany
        d. Host Path: /pv/data-analytics

`
kubectl apply -f - <<EOF
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-analytics
spec:
  capacity:
    storage: 100Mi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Recycle
  storageClassName: slow
  mountOptions:
    - hard
    - nfsvers=4.1
  hostPath:
    path: /pv/data-analytics
EOF
`

11. Create a Pod called redis-storage-yourname with image: redis:alpine 
	with a Volume of type emptyDir that lasts for the life of the Pod. specs:.
        a. Pod named 'redis-storage-yourname' 
        b. Pod 'redis-storage-yourname' uses Volume type of emptyDir
        c. Pod 'redis-storage-yourname' uses volumeMount with mountPath = /data/redis

`
kubectl ...
`

12. Create this pod and attached it a persistent volume called pv-1
        a. Make sure the PV mountPath is hostbase : /data

```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: use-pv
  name: use-pvspec-yourname
  containers:
  - image: nginx
    name: use-pv
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```

`
amswer-12.yaml
`
<<<<<<< HEAD
<<<<<<< HEAD

13. Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. 
=======
=======
>>>>>>> parent of 9985019 (answer example)
    13. Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. 
>>>>>>> parent of 9985019 (answer example)
	Record the version. 
	Next upgrade the deployment to version 1.17 using rolling update. 
	Make sure that the version upgrade is recorded in the resource annotation.
        a. Deployment : nginx-deploy. Image: nginx:1.16
        b. Image: nginx:1.16
        c. Task: Upgrade the version of the deployment to 1:17
        d. Task: Record the changes for the image upgrade

`
answer13.yaml
kubectl ...
`
<<<<<<< HEAD
<<<<<<< HEAD

14. Create an nginx pod called nginx-resolver using image nginx, 
=======
=======
>>>>>>> parent of 9985019 (answer example)
    14. Create an nginx pod called nginx-resolver using image nginx, 
>>>>>>> parent of 9985019 (answer example)
	expose it internally with a service called nginx-resolver-service. 
	Test that you are able to look up the service and pod names from within the cluster. 
	Use the image: busybox:1.28 for dns lookup. 
	Record results in /root/nginx-yourname.svc and /root/nginx-yourname.pod
`
kubectl or YAML file
nginx-yourname.svc
nginx-yourname.pod
`
<<<<<<< HEAD
<<<<<<< HEAD

15. Create a static pod on node01 called nginx-critical with image nginx. 
=======
=======
>>>>>>> parent of 9985019 (answer example)
    15. Create a static pod on node01 called nginx-critical with image nginx. 
>>>>>>> parent of 9985019 (answer example)
	Create this pod on node01 and make sure that it is recreated/restarted automatically in case of a failure.

`
answer-15.yaml
`


16. Create a pod called multi-pod with two containers.
	Container 1, name: alpha, image: nginx
	Container 2: beta, image: busybox, command sleep 4800.
        a. Environment Variables:
            i. container 1:
            ii. name: alpha

            iii. Container 2:
            iv. name: beta


`
answer-16.yaml
`

