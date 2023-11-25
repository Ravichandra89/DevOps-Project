<div align="center">
  <img src="./public/assets/DevSecOps.png" alt="Logo" width="100%" height="100%">

  <br>
  <a href="http://netflix-clone-with-tmdb-using-react-mui.vercel.app/">
    <img src="./public/assets/netflix-logo.png" alt="Logo" width="100" height="32">
  </a>
</div>

<br />

<div align="center">
  <img src="./public/assets/home-page.png" alt="Logo" width="100%" height="100%">
  <p align="center">Home Page</p>
</div>

# Deploy Netflix Clone on Cloud using Jenkins - DevSecOps Project!

### **Phase 1: Initial Setup and Deployment**

**Step 1: Launch EC2 (Ubuntu 22.04):**

- Provision an EC2 instance on AWS with Ubuntu 22.04.
- Connect to the instance using SSH.

**Step 2: Clone the Code:**

- Update all the packages and then clone the code.
- Clone your application's code repository onto the EC2 instance:
    
    ```bash
    git clone https://github.com/Ravichandra89/DevOps-Project.git
    ```
    
**Step 3:  Install Docker and Run the App Using a Container:**

- Setup Docker on EC2 instance.
    ```bash
     sudo apt-get update
     sudo apt-get install docker.io -y
     sudo systemctl start docker
     sudo systemctl enable docker
    ```

-Build and run your application using Docker containers:
- Open DevOps project cloned directory then follow this commands.
- Add port 8081 to your security group.
  
  ```bash
     docker build -t netflix .
     docker run -d --name netflix -p 8081:80 netflix:latest

  # To make Image with TMDB API delete the container and image and again make

     docker rmi netflix
     docker stop <container id>
     docker rm -f netflix
  ```
** Note :- It will show an error cause you need API key**

** Step 4: Docker image with API key**
- Follow the given key :-

  ```bash
    docker build --build-arg TMDB_V3_API_KEY=<your-api-key> -t Netflix .
  ```
- Run container again from Netflix image
  ```bash
    docker run -d --name netflix -p 8081:80 Netflix 
  ```
- To access this copy your public IP address https://your_ip:8081


