# Deployment of test application on K8s cluster

To deploy the manifests enter below command:
```shell
$ kubectl create ns test-nodejs
$ kubectl apply -f k8s-manifests/nodeApp-deploy.yml -ntest-nodejs
$ kubectl apply -f k8s-manifests/nodeApp-service.yml -ntest-nodejs
```

Above commands will create:
1. A Kubernetes namespace with name test-nodejs
2. A deployment running Node JS based Hello World application
3. A service of type NodePort for above deployment

# Autoscaling the deployment using HPA

To autoscale the created deployment:
```shell
$ kubectl apply -f k8s-manifests/nodeApp-hpa.yml -ntest-nodejs
```

Above command will create an HPA resource which will scale the count
of pods for mentioned deployment based on 80-80% of cpu or memory
metrics.

