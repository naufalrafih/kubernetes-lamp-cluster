# kubernetes-lamp-cluster
Deploy LAMP stack on Kubernetes Cluster using kind <br>
Step by step:

1. Create kind cluster <br>
Optional: Create multi-node cluster using [config file](kind-config.yaml) <br>
```kind create cluster --config kind-config.yaml```

2. Create secret using [secrets file](secrets)

3. Create all 4 manifests on [lamp-stack folder](lamp-stack) <br>
```kubectl create -f [FILENAME].yaml```

4. Copy [index.php](lamp-stack/index.php) file to php container <br>
```kubectl cp index.php [LAMP_POD_NAME]:/app -c php-container``` <br>
```kubectl exec -it [LAMP_POD_NAME] -c php-container -- cat /app/index.php```

5. Expose the service to the preferred port
```kubectl port-forward service/[LAMP_SERVICE_NAME] [PORT]:80```

6. Open ```localhost:[PORT]``` in your browser
