# Build nodejs application locally .

1. Clone the git repo https://github.ibm.com/arjsbabu/bootcamp2019nodejs

2. Navigate to git folder and build the application using command  "docker build -t yourusername/nodewebapp:v1.0 ."

3. Run  "docker images"  to see the created image

4. To test the image locally run docker run -p 49160:8080 -d yourusername/nodewebapp:v1.0

5. Test application using "curl localhost:49160"

# Push the newly created Docker image to the IBM Cloud private container registry

6. Log in to your IBM Cloud account. Include the --sso option if using a federated ID. 
  "ibmcloud login -a cloud.ibm.com -r au-syd -g Default"

7. Find your namespace by listing all the namespace in the registry "ibmcloud cr namespaces"

8. If you have a namespace, make note of the name. If you don't have one, create it "ibmcloud cr namespace-add <My_Namespace>"

9. Identify your Container Registry by running "ibmcloud cr info". Container registry name is needed during tag the Docker image to pus   h from your local to Container Registry.

10. List if any Docker image exist in registry by running "ibmcloud cr images"

11. List your local Docker images by running "docker images"

12. Tag your local Docker image using command "docker tag  yourusername/nodewebapp:v1.0  container-registry_url/namespace/yourusername/nodewebapp:v1.0

13. Login to IBM Container registry using command "ibmcloud cr login"

14. Push Docker image to IBM Container registry using command "docker push container-registry_url/namespace/yourusername/nodewebapp:v1.0"

# Deploy the application using  Kubernetes dashboard

15. Steps https://github.ibm.com/karan-singh/tschoollab/blob/master/Simple-GUI-Deploy.md

or 

# Deploy application to Kuberbetes cluster using helm chart

16. Create a role and role binding for helm client to work properly

    kubectl create -f role.yaml -f rolebinding.yaml -n default

17. Initialize Helm by running the "helm init --tiller-namespace default" command in your cluster.

18. Navigate to "chart/nodejs" and update the values.yaml with image repository and tag.

19. Install a Helm chart by run the command helm install --name nodejs . --tiller-namespace default

20. Get the deployed resources and verify using kubectl commandline

21. Find the public IP of worker node by running command "ibmcloud cs workers clustername"
