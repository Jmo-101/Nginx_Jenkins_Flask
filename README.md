<p align="center">
<img src="https://github.com/kura-labs-org/kuralabs_deployment_1/blob/main/Kuralogo.png">
</p>
<h1 align="center">Nginx_Jenkins_Flask<h1> 

## Planning:


# About:

This project showcases the use of Jenkins, nginx, while also using git commands in the command line in order to push edited files to our repositories. Also showcased was the use of AWS CloudWatch in order to monitor the metrics of our application.

## EC2:

We manually created an EC2 instance on AWS with an instance type of T2.medium. We also adjusted our security groups and added four security groups to our instance, which are going to be used later on. The next step in the EC2 instance was to install Jenkins, as well as a python3 virtual environment (`python3.10-venv`), `python3-pip`, and `nginx`. Once nginx was installed we had to edit the configuration file and change our application location port in order for port 8000 to be used on it.

<img width="250" alt="Screenshot 2023-10-02 at 12 44 07 PM" src="https://github.com/Jmo-101/Nginx_Jenkins_Flask/assets/138607757/7be3bd2c-d304-4cac-b40a-49505f29c184">

<img width="250" alt="Screenshot 2023-10-02 at 9 04 27 PM" src="https://github.com/Jmo-101/Nginx_Jenkins_Flask/assets/138607757/7fc7cdc8-a863-499f-b615-ed4665df29de">

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

# Github:

I initially used `git clone` to clone a repository into the instance. From there, I moved the files using `mv` in the command line to move the files I needed into the repository I made. 

Afterwards, I needed to make a second testing branch using `git checkout -b testing_branch`. From there, I made the necessary changes to the Jenkins file and merged it back to the main branch using `git merge`. 

Once the two branches were merged, I used the command `git commit` to commit any changes made to the existing files. I used `git status` to check the status of the branch. Once I was satisfied with the changes, I used `git push` to push the files into the local repository.


<img width="250" alt="Screenshot 2023-10-02 at 12 01 35 PM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/c61b5db4-1437-403c-93c5-af354037b962">
<img width="250" alt="Screenshot 2023-10-02 at 11 55 00 AM" src="https://github.com/Jmo-101/Web_Hook_Flask/assets/138607757/0bc5607e-dea9-4b4e-80c6-ebceeb04537b">

## CloudWatch:

I installed a CloudWatch agent into my application in order to monitor the metrics used such as CPU and memory. I installed the agent using a series of commands in the command line. Once that was installed I had to configure the agent in order to track the metrics I wanted it to track.
