## Blue Ocean Overview
  - Optimizes GUI for pipelines
  - Re-skins Jenkins to make management easier
  - Has built-in diagnostics
  
## Blue Ocean Setup Summary
  - One repo per project
  - Git repos can be re-used in multiple pipelines
  - Make Jenkins become IasC (Infrastructure as Code)
  
## Adding a GitHub repo to a Pipeline
In order to store Jenkins configurations as code it is necessary to use pipelines.
## Development and Staging Pipeline Summary
  - Development pipelines are kicked off very frequently and with continuous deployment will automatically update servers
  - Staging is where QA will test the environment so this needs to be kept more static to prevent interruptions
## Multi-Pipeline Summary
  - There is no limit on the number of pipelines you can have.
  - Optimize for your environment - every setup is different.
  - Be careful with continuous deployment because you may overwrite the wrong thing.
## Triggers Demo
Now let’s take a look at setting up a trigger, so we will continuously, “automagically,” check if our GitHub software has been updated, triggering the pipeline processes.   
## Pipeline Triggers Walkthrough
  - When code is pushed to the Git repository after a pull request, build automatically, i.e. continuously integrate
  - If the tests in a pipeline pass, deploy the code, i.e. continuously deploy
## Testing - Key ideas
  - Linting is testing to check for syntax errors in code.
  - Security testing can be performed with a variety of software to test for CVE vulnerabilities.
  - Performance testing is done by setting up a smaller scale environment than production with Jenkins and running simulated host calls   - into that environment to see how it performs under load.
  - Integration testing is testing code from different modules to make sure it all works together.  
## Security Testing with Aqua
Aqua is a Jenkins plugin designed for testing Docker containers. It is one of many security vulnerability scanners available, testing against CVE (Common Vulnerabilities and Exposures).

## We’ll install and show how to use Aqua next.  
  - Aqua Testing Summary
  - Aqua is used for scanning Docker containers for CVE
  - Aqua depends on Docker
  - Aqua can be integrated into a testing pipeline in the Continuous Integration stage  
## Further Research on Testing
If you’d like to look into other types of tests, here are some resources:
- Performance Testing:
https://opensource.com/life/16/7/running-jmeter-jenkins-continuous-delivery-101
- Integration Testing:
https://www.twilio.com/engineering/2017/01/09/how-to-setup-a-ci-build-for-integration-tests

## Blue/Green Deployment Strategy
  - `apt install ansible`
  - `pip install boto`
  - Jenkins plugin CloudBees AWS Credentials Plugin
  - Configure AWS Credentials in Jenkins
  - Map credentials from Jenkins to Pipeline application
 ## Blue/Green Deployment IAM Policy
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:*",
                "cloudwatch:*",
                "route53:*",
                "ec2:*",
                "ec2:DescribeAccountAttributes",
                "elasticloadbalancing:*"
            ],
            "Resource": "*"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "arn:aws:iam::*:role/aws-service-role/*"
        }
    ]
}
``` 
## Blue/Green Deployment Strategy (cont.)
  - Set up Private Route53 Zone
  - Configure Healthcheck
  - Run Blue Deployment
  - Run Green Deployment
  - Check Route53 entries  
## Deployment Strategies Guide
  - Manual changes will get you in trouble sooner or later.
  - New feature code releases often require blue/green deployment due to scheme changes and/or to keep consistency.
  - To perform a bug fix of an existing product, a rolling deployment will be your most frequent choice.

