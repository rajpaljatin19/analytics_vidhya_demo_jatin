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

![image](https://user-images.githubusercontent.com/32235493/214910793-6d8c6b0d-aa4e-4a6e-be45-be8843381f73.png)

If you run `kubectl get pods -w` you'd be able to see the pod changes its `STATUS` from `RUNNING` to `COMPLETED`

![image](https://user-images.githubusercontent.com/32235493/214910593-939466a1-938a-40a8-bb6d-05faacbc63b7.png)

5. Check the logs of your Pod

`kubectl logs pipeline-pod`

![image](https://user-images.githubusercontent.com/32235493/214910383-b76e6bca-0fe7-4e3d-b1ce-2649ebf32391.png)
