# Assignment_nginx
Created a terraform deployment to host a stateless application in AWS Prerequisites Terraform installed in configured in my system AWS CLI configured Docker engine Steps I used during this are as follows:

I have created a docker file (Docker file) and created a basic index.html page

I have build the image and ran the docker container in the local machine and then used http://localhost:8080 to confirm if the container is running properly.

Then I have created an AWS account and downloaded the access credentials.

The next steps I started creating the main.tf file for Terraform, the following resources I created using the terraform scripts

I provided AWS resource provider from hasicorp

Then added my default AWS region and my IAM access keys which I already had downloaded

Then I created a docker image, before contnuing to the next steps I pushed my docker image from local to docker hub.

I created SG for the LB for the ports required for the application to run and then created LB listners and target groups.

The next step I created a security group for the aws services so that traffic is only allowed from the LB security group.

The next step I added the output parameter to get the LB url to open the application

After creation of the main.tf file,run the below commands-

terraform init (to nitializes a working directory and downloads the necessary provider plugins.)

terraform validate (to check if all is good in the main.tf file)

terraform fmt (To format configuration files into a canonical format and style.)

terraform plan (to see all the resources that are getting created)

terraform apply (to create all the resources in AWS)

THen I created K8S master and node cluster Using KOPS - Below is the requirements-

kops create cluster --name=pwdinfo.xyz \
--state=s3://pwdinfo.xyz --zones=us-east-1a,us-east-1b,us-east-1c \
--node-count=3 --master-count=3 --node-size=t2.medium --master-size=t2.medium \
--master-zones=us-east-1a,us-east-1b,us-east-1c --master-volume-size 10 --node-volume-size 10 \
--ssh-public-key=/root/.ssh/id_rsa.pub \
--dns-zone=pwdinfo.xyz --dry-run --output yaml

Then I pull the image from docker hub to k8s node servers.
docker push <iamge name>
docker run -it --image name.
then-
kubectl get pod (Show the status of running pods)

The next step I added the output parameter to get the LB url to open the application

terraform destroy (to stop and remove all the resources)
