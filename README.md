## MERN APP Kubernetes without react and nodejs

Uisng Mongodb as backend and mongo express as frontend

Ensure minikube and kubectl are installed
- brew install kubectl
- brew install minikube

After writing the yaml files, start minikube and apply the files;
- minikube start
- kubectl apply -f mongo-config.yaml
- kubectl apply -f secret.yaml
- kubectl apply -f mongo-app.yaml
- kubectl apply -f web-app.yaml

Check that its all been succesfully deployed
- kubectl get pod
- kubectl get configmap
- kubectl get secret
- kubectl get svc

To check the ip of the minikube run;
- minikube ip

To see the app on your browser;
- kubectl get node -o wide
- minikube service <servicename> (webapp-service)

ps: if you encounter error "Because you are using a Docker driver on darwin, the terminal needs to be open to run it."
run ps -ef | grep docker@127.0.0.1
it should give an output similar to this: 501 53910 53883   0  7:31PM ttys004    0:00.02 ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -N docker@127.0.0.1 -p 65105 -i /Users/xxx/.minikube/machines/minikube/id_rsa -L 59452:10.100.87.17:8081

copy the tunnel port, 59452, open your boswer and paste 127.0.0.1:59452
kubectl delete deployment --all
kubectl delete secret --all
