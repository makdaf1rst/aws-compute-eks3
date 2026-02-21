[README.md](https://github.com/user-attachments/files/25461081/README.md)
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks3)

**Author:** saqibh49@gmail.com  
**Email:** saqibh49@gmail.com

---

## Create Kubernetes Manifests

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I will create Deployment and Service manifest files that tell Kubernetes how to run and expose my backend application. I'm doing this project because knowing how to write manifests is how you actually tell Kubernetes what to do — without them, my cluster wouldn't know what containers to run or how users can access them.

### Tools and concepts

I used Amazon EKS, eksctl, EC2, Docker, ECR, Git, and kubectl to deploy a containerized backend application to a Kubernetes cluster. Key concepts include using manifests to define how Kubernetes runs and exposes my app, building and pushing Docker images to ECR, and understanding how Deployments and Services work together to keep an app running and accessible.

### Project reflection

I chose to do this project today because understanding Kubernetes manifests is essential for deploying real applications, and I wanted to get comfortable writing Deployment and Service files myself. Something that would make learning with NextWork even better is if there was a quick reference sheet for common manifest configurations so I can start writing them from memory instead of always looking things up.

This project took me approximately 45 minutes. The most challenging part was figuring out the commands to make without first looking at the guide.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included connecting to my EC2 instance, installing eksctl, attaching an IAM role with AdministratorAccess to my instance, and running the eksctl create cluster command to spin up a cluster with 3 t3.micro nodes in us-east-2.

### Backend code

I retrieved the backend that I plan to deploy by installing Git on my EC2 instance and cloning the repository from GitHub. The backend is the part of an application that handles the logic, data processing, and communication with other services — basically everything that happens behind the scenes that the user doesn't see.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes deploys applications as containers, so the app needs to be packaged into an image first. I used Docker to build the image, tagging it with my ECR repository URL so it's ready to be pushed and pulled by my cluster.

I also pushed the container image to a container registry, because my EKS cluster needs to pull the image from a central location when it's time to deploy. To push the image to ECR, I created a repository, logged Docker into ECR, tagged my image with the repository URL, and then ran the docker push command to upload it.

---

## Manifest files

Kubernetes manifests are configuration files that tell Kubernetes what to deploy and how to deploy it. Manifests are helpful because instead of manually running commands to set everything up, you just write out what you want in a file and Kubernetes handles the rest — making deployments repeatable, consistent, and easy to update.

A Kubernetes deployment manages how my application runs on the cluster — it handles things like how many copies of the app to run, which container image to use, and automatically replaces any containers that crash. The container image URL in my Deployment manifest tells Kubernetes exactly where to pull the app's image from, in my case, my ECR repository.

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes your application to the network so users or other services can actually reach it. You need a Service manifest to define how traffic gets routed to your containers — without one, your app is running but has no way for anyone to connect to it.

My Service manifest sets up a NodePort Service called nextwork-flask-backend that routes traffic on port 8080 to my backend containers. The selector matches it to any pods labeled nextwork-flask-backend, and NodePort means it opens a port on each node so the app can be accessed from outside the cluster.

![Image](http://learn.nextwork.org/grateful_white_lucky_bat/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

---

---
