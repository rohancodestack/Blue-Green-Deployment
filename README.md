# Blue-Green-Deployment
This repository demonstrates a Blue-Green deployment strategy using Kubernetes and Jenkins. It provides a seamless way to release new versions of an application while minimizing downtime and reducing the risk during deployments.

**Features**
Blue-Green Deployment: Safely deploy new versions of an application by running two identical environments—blue and green.
Jenkins Pipeline Integration: Automate the deployment process using a Jenkins pipeline defined in the Jenkinsfile.
Maven-based Java Application: The project is built using Maven (pom.xml), making it easy to manage dependencies and build lifecycle.
Kubernetes Configuration: The repository contains YAML files for deploying the application on Kubernetes:
app-deployment-blue.yml
app-deployment-green.yml
bankapp-service.yml
mysql-ds.yml
Docker Support: A Dockerfile is provided for containerizing the application.

**Prerequisites**
Docker: To build and run the application inside containers.
Kubernetes: For managing the Blue-Green deployments.
Jenkins: To automate the deployment process using the pipeline.
Maven: For building the Java application.

Setup Instructions

1. **Clone the Repository**

git clone https://github.com/yourusername/Blue-Green-Deployment.git
cd Blue-Green-Deployment


2. **Build the Application
Build the Java application using Maven:**

./mvnw clean install
3. Deploy to Kubernetes

**Apply the Kubernetes manifests to deploy both the blue and green environments:**
kubectl apply -f app-deployment-blue.yml
kubectl apply -f app-deployment-green.yml
kubectl apply -f bankapp-service.yml
kubectl apply -f mysql-ds.yml

4. **Jenkins Pipeline**
The Jenkinsfile contains the pipeline definition for automating the Blue-Green deployment process.

- To set up Jenkins:
Create a new pipeline job in Jenkins.
Point the pipeline to this repository.
Configure Jenkins to trigger deployments based on version changes or other criteria.

5. **Docker Setup**
To build and run the Docker image locally:

docker build -t blue-green-app .
docker run -p 8080:8080 blue-green-app

**Blue-Green Deployment Strategy**

Blue Environment: The current production environment.
Green Environment: The new version of the application, which is tested before switching traffic from blue to green.

**Folder Structure**

.mvn/: Maven wrapper files.
Cluster/: Contains additional configuration files for the Kubernetes cluster.
Dockerfile: Dockerfile for containerizing the application.
Jenkinsfile: Jenkins pipeline definition for automating the deployment.
src/: Java source code for the application.
YAML files (app-deployment-blue.yml, app-deployment-green.yml, etc.): Kubernetes manifests for deploying the application.

Contributing
Feel free to submit pull requests or open issues for any bugs or improvements.

License
This project is licensed under the MIT License.
