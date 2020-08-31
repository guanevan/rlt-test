Tasks and solutions:

Task 1) Create Terraform code to deploy a Kubernetes cluster inside of GCP. 
Solution:

/* After enable kubernetes Engin API in  GCP; Clone repository from https://github.com/guanevan/rlt-test.git ; In googl cloud shell */

git init

git clone https://github.com/guanevan/rlt-test.git

cd terraform-gke 

terraform init

terraform plan

terraform apply

Task 2) Build rlt-test application image and push GCR

Solution:

cd terraform-gke/app/

docker build -t rlt-app:1.0 .

docker tag rlt-app:1.0 us.gcr.io/third-opus-287905/rlt-app:1.0

docker push us.gcr.io/third-opus-287905/rlt-app:1.0

Task 3) Deploy the helm chart included in the repo into the kubernetes cluster.  

Solution:

helm rlt-test

cd rlt-test 

/ * copy all files/dirs from my git exclude terrafor-gke to rlt-test dir and overwrite files with same name */

helm lint 

cd ..

helm package rlt-test 

helm install rlt-test rlt-test-0.1.0.tgz

/ * use kubectl get all, kubectl get service, kubectl get ingress to check status  */

kubectl logs pod-name, kubectl describe pod pod-name to check errors

Task 4) Fix any issues that may be present in the helm chart.

/* Pod was able to pull image from GCR and start but forced to restart with error. was troubleshooting ... */

Task 5) Expose the application to the outside world.  

