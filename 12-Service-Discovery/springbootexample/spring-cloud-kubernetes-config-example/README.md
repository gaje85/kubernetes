# Spring Cloud Kubernetes Config Example


## Commands
- make sure maven is installed . if not run the command apt install maven
- build the project mvn clean install
- login to docker hub using docker login 
- `skaffold run --default-repo gaje85` - For build and run
- The above command will fail. Replace the image name from the above command logs in deploy.yaml file and rerun
   when we rerun the image will be builded again and pushed to the docker hub repo . In this command replace my repo name with docker hub to yours --default-repo <your docker repo name>

- `kubectl apply -f config.yaml` - For applying the ConfigMap changes
- `kubectl describe configmap config-example` - For describing the contents of Config Map
- `kubectl logs <pod_name> -f` - For tailing the logs from the pod
