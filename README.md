# AsciiArtify
Learn Project for Prometheus (Devops). Generating with AI

## Example (Linux):
```shell
kubectl kubectl-ai "some prompt"
```

|NAME| PROMPT                                                                         | Description | EXAMPLE |
|----|--------------------------------------------------------------------------------|-------------|---------|
|app | "create gcr.io/shkirmantsev/demo:v1.0.0 pod with name app and container name app. container port 8000 with name http. Labels app=demo and run=demo"| pod |app.yaml |
|app-livenessprob | "create gcr.io/shkirmantsev/demo:v1.0.0 pod with name app-livenessprob and container name app. container port 8080 with name http. Namespace demo. livenessProbe on port 8000 and path '/'"| pod with probe |app-livenessprob.yaml |
|app-readinessprob | "create gcr.io/shkirmantsev/demo:v1.0.0 pod with name app-readinessprob and container name app. Port 8000 with name http. livenessProbe ('/') and readinessProbe ('/ready') on 8000 port with period, delay and threshold"| pod with probe |app-readinessProbe.yaml |
|app-volume | "create gcr.io/kuar-demo/kuard-amd64:1 pod with name app-volume and container name app. Port 8080 with name http. livenessProbe ('/healthy') and readinessProbe ('/ready') on 8080 port with period, delay and threshold. Volume 'data', hostPath '/var/lib/app'"| pod |app-volumeMounts.yaml |
|app-cronjob | "create CronJob with name app-cronjob and container name hello. Starting each 5 min. Container image is bash. Container command 'echo', 'Hello world', restartPolicy: OnFailure"| cronjob |app-cronjob.yaml |
|app-job-rsync | "create Job with name app-job-rsync and container google/cloud-sdk:275.0.0-alpine with name init.volumeMaunt 'data-input'. gcePersistentDisk glow-data-disk-200, fsType 'ext4'.Command '/bin/sh', '-c', 'gsutil -m rsync -dr gs://glow-sportradar/ /data/input', restartPolicy: Never, backoffLimit: 0"| job |app-job.yaml |
|app-multi-containers | "create pod with name app-multi-containers, with nginx container(1st) and . debian container (2nd). Communication between containers through 'html' volume. 2nd container wright date to '/html/index.html', 1st container uses this page as /usr/share/nginx/html"| pod |app-multicontainer.yaml |
|app-resource | "create gcr.io/kuar-demo/kuard-amd64:1 pod with app-resource and container name app. Port 8080 with name http. livenessProbe ('/healthy') and readinessProbe ('/ready') on 8080 port with period, delay and threshold. Resources cpu '100m', memory '128Mi', limited by '100m' and '256Mi'"| pod with resource|app-resources.yaml |
|app-secret-env | "create pod (from 'redis' image) with name app-secret-env and container name mycontainer. restartPolicy: Never. Secret environment variables SECRET_USERNAME (secretKeyRef, name mysecret1, key username) and SECRET_PASSWORD (secretKeyRef,name mysecret1, key password)"| pod with secret |app-secret-env.yaml |