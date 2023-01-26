# analytics_vidya_demo_jatin

Steps to try out the demo yourself

1. On your machine, start minikube. which is a local Kubernetes cluster where in you can try your demo deployments. if you need instruction to download & setup minikube for your machine's OS, please check minikube documentation [here](https://minikube.sigs.k8s.io/docs/start/)

`minikube start`

![image](https://user-images.githubusercontent.com/32235493/214908056-f636a0ea-b5e9-4889-bc1b-31dc4560419b.png)

2. Run kubectl apply to configure configmaps for both pipeline data and configs

`kubectl apply -f cfg-configmap.yaml`

`kubectl apply -f data-configmap.yaml`

3. Now run your Kubernetes Pod which will is nothing but Benthos container to run your cloud native data pipeline

`kubectl apply -f pod.yaml`

4. Check the pod status

`jatinrajpal@Jatins-MacBook-Air cloud_native_data_pipelines % kubectl get pods`

`NAME              READY   STATUS              RESTARTS   AGE`

`pipeline-pod      0/1     Completed           0          5s`

If you run `kubectl get pods -w` you'd be able to see the pod changes its `STATUS` from `RUNNING` to `COMPLETED`

`jatinrajpal@Jatins-MacBook-Air cloud_native_data_pipelines % kubectl get pods -w`

`NAME              READY   STATUS              RESTARTS   AGE`

`pipeline-pod      0/1     ContainerCreating   0          4s`

`spark-pi-driver   0/1     Error               0          102d`

`pipeline-pod      1/1     Running             0          4s`

`pipeline-pod      0/1     Completed           0          5s`

5. Check the logs of your Pod

`kubectl logs pipeline-pod`
![image](https://user-images.githubusercontent.com/32235493/214910383-b76e6bca-0fe7-4e3d-b1ce-2649ebf32391.png)
