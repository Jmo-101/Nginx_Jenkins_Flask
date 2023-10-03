<p align="center">
<img src="https://github.com/kura-labs-org/kuralabs_deployment_1/blob/main/Kuralogo.png">
</p>
<h1 align="center">Nginx_Jenkins_Flask<h1> 

## Planning:
<img width="500" alt="Screenshot 2023-10-03 at 1 59 35 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/4d165a0f-1660-4c0e-b468-0c4c0fa8f994">

# About:

This project showcases the use of Jenkins, nginx, while also using git commands in the command line in order to push edited files to our repositories. Also showcased was the use of AWS CloudWatch in order to monitor the metrics of our application.

## EC2:

We manually created an EC2 instance on AWS with an instance type of T2.medium. We also adjusted our security groups and added four security groups to our instance, which are going to be used later on. The next step in the EC2 instance was to install Jenkins, as well as a python3 virtual environment (`python3.10-venv`), `python3-pip`, and `nginx`. Once nginx was installed we had to edit the configuration file and change our application location port in order for port 8000 to be used on it.

<img width="250" alt="Screenshot 2023-10-02 at 12 44 07 PM" src="https://github.com/Jmo-101/Nginx_Jenkins_Flask/assets/138607757/7be3bd2c-d304-4cac-b40a-49505f29c184">

<img width="250" alt="Screenshot 2023-10-02 at 9 04 27 PM" src="https://github.com/Jmo-101/Nginx_Jenkins_Flask/assets/138607757/7fc7cdc8-a863-499f-b615-ed4665df29de">


# Git:

I initially used `git clone` to clone a repository into the instance. From there, I moved the files using `mv` in the command line to move the files I needed into the repository I made. 

Afterwards, I needed to make a second testing branch using `git checkout -b testing_branch`. From there, I made the necessary changes to the Jenkins file and merged it back to the main branch using `git merge`. 

Once the two branches were merged, I used the command `git commit` to commit any changes made to the existing files. I used `git status` to check the status of the branch. Once I was satisfied with the changes, I used `git push` to push the files into the local repository.


<img width="250" alt="Screenshot 2023-10-02 at 12 01 35 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/c61b5db4-1437-403c-93c5-af354037b962">
<img width="250" alt="Screenshot 2023-10-02 at 1 48 10 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/1d05c7a3-2ab3-4986-ae1d-84dcdca73b16">
<img width="250" alt="Screenshot 2023-10-02 at 11 55 00 AM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/0bc5607e-dea9-4b4e-80c6-ebceeb04537b">

## CloudWatch:

I installed a CloudWatch agent into my application in order to monitor the metrics used such as CPU and memory. I installed the agent using a series of commands in the command line. Once that was installed I had to configure the agent in order to track the metrics I wanted it to track.

<img width="400" alt="Screenshot 2023-10-02 at 12 58 53 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/cc7d8a96-7323-403b-8b19-38b06b162c24">
<img width="300" alt="Screenshot 2023-10-02 at 1 01 51 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/7719dd89-ee61-4245-a6e1-2cb87c2ff3fb">
<img width="300" alt="Screenshot 2023-10-02 at 1 02 31 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/8da03b1e-17be-469a-8a73-c5af5d511310">
<img width="400" alt="Screenshot 2023-10-02 at 1 31 37 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/29034810-629a-487a-afd9-1001d32791b7">
<img width="300" alt="Screenshot 2023-10-02 at 1 14 26 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/670b9b1b-4b3c-4ed1-92bb-93815b0a87db">

Once CloudWatch was installed in the instance I traversed over to AWS to monitor the CPU usage of the application. I noticed when Jenkins ran the pipeline the cpu usage for the application went up. With that knowledge i came to the conclusion that a t2.micro instance would not be able to hand this application specifically.

<img width="300" alt="Screenshot 2023-10-02 at 1 59 24 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/ea539c47-319b-4a4b-9527-9aba08e14ca5">


# Jenkins:

Once the GitHub repository was set up, I moved on to initializing Jenkins. Using commands in the command line, I set up Jenkins to build a multibranch pipeline for my application. During the Jenkins setup, I also installed the "Pipeline Keep Running Step" plugin

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install fontconfig openjdk-11-jre
sudo apt-get install Jenkins
```

<img width="600" alt="Screenshot 2023-10-02 at 12 18 47 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/bad4ac00-d11e-4c93-811b-3a0a839eb856">

<img width="600" alt="Screenshot 2023-10-02 at 1 55 03 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/e6e5d3fb-d7ab-4d2b-9b31-e4c3f90a333d">

