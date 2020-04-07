# Welcome to the Cloud DevOps CI/CD Course!
To facilitate software development, Continuous Integration / Continuous Development (CI/CD) has become a swiss army knife of development, deployment, and testing. One of the most popular and oldest currently maintained frameworks for CI/CD is called Jenkins.

Jenkins comes originally from the Hudson project which had very similar features and functionality, but was controlled by Sun Microsystems. Jenkins was released in 2011 and is open source. In addition, Jenkins is highly modular and supports a multitude of plugins. We will cover a few of the plugins at a higher level in this course.

Most of our focus in CI/CD will be on pipelines. With pipelines we are able to use code checked into a Git repository to control the execution, linting, security testing, and performance testing of code. Within the course we will also explore using multiple branches for different levels such as development, staging, and production.

## Course Overview Skills Check
This course is taught with the assumption that you have completed courses 1 and 2 of the Cloud DevOps Nanodegree. We will move very quickly over sections which cover the same material addressed in those previous courses, and reinforce your understanding of them.

The fundamentals of AWS are addressed in previous courses. You are assumed to have had some experience using the command line in a Linux or UNIX environment. New subject matters such as Jenkins, Pipelines, Prometheus, and Ansible are taught with the expectation that you have no experience with them. We will attempt to review material very frequently in the form of short quizzes and practice exercises to ensure you are mastering the skills and concepts. You will learn by doing, in the Udacity way!
## Course Overview
I am excited that we will be able to address a wide variety of subject matter throughout this course! Our main focus will be on CI/CD and pipelines in the first two lessons of this course. Next we will move to configuration management using Ansible, and we will conclude with monitoring and log aggregation.

The idea for you as a student is to be able to develop the skills needed to: a) create an environment from code (infrastructure as code) with Ansible; b) create a development pipeline on this infrastructure with Jenkins; and c) monitor and maintain this infrastructure through the use of monitoring, metrics, and log analytics using Prometheus and ELK stack.

One of the beautiful things about the field of DevOps is the flexibility and interoperability of the different components, which can be compared to Lego pieces. In these lessons we will start to understand how the building blocks of development, monitoring, and deployment fit together and complement each other.

It should also be noted that we are endeavoring to use some of the most common representations of these technologies. There are many very similar, but different, pieces of software which perform the same or similar tasks. When will discuss some but not all of these alternatives.

## Create an IAM user 
  - create policy
  - create usergroup 
  - create user
  - lanch EC2 with ubunto systme
## Commands for Installing Jenkins
```
sudo apt-get update
sudo apt install -y default-jdk
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install -y jenkins
```
## Installing the Blue Ocean Plugin
login to jenkins and install Blue ocen plugins

## CI / CD Definitions

### Definitions
Continuous Integration (CI) is a development practice where developers integrate code into a shared repository frequently, preferably several times a day. Each integration can then be verified by an automated build and automated tests.
Source: [https://codeship.com/continuous-integration-essentials](https://codeship.com/continuous-integration-essentials)

Continuous deployment (CD) is a strategy for software releases wherein any code commit that passes the automated testing phase is automatically released into the production environment, making changes that are visible to the software's users
[https://searchitoperations.techtarget.com/definition/continuous-deployment](https://searchitoperations.techtarget.com/definition/continuous-deployment)

### CI / CD Diagram
![CI / CD Diagram](./img/screen-shot-2019-07-30-at-7.05.20-pm.png)
### Pipelines Overview
One of the key best practices of DevOps is to be able to do “Infrastructure as Code”. A pipeline enables us to store our Jenkins project configuration as code in a Git repository.

The previous way of doing this was to store the configurations as text on the Jenkins server. However, it is far superior to store this in a Git repository, because that way we version it, review it, perform pull requests, and integrate it just like the rest of our code.

A pipeline contains steps which have different actions performed as part of those steps.


