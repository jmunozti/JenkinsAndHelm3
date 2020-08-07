# JenkinsAndTerraform

This is a Jenkins Pipeline to deploy AWS resources using Terraform.

# Requirements

1.- Jenkins and Terraform must be installed in advance.

2.- Your email SMTP server in Jenkins must be configured correctly.

3.- You have to create an AWS S3 bucket to enable remote state storage. https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html

4.- You have to create a AWS EC2 Key to prove your identity when connecting to an instance.

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair

# Usage

Watch the video: https://github.com/jmunozti/JenkinsAndTerraform/raw/master/JenkinsAndTerraform.mp4

1.- Run Jenkins.

2.- Create a new Jenkins Pipeline.

3.- Configure your pipeline.

Go to the option This project is parameterized, enable it, and add two password parameters "AWS_ACCESS_KEY_ID" and "AWS_SECRET_ACCESS_KEY".

Go to Pipeline -> Definition and choose "Pipeline script form SCM".

In the same section, go to SCM and choose "Git"

In the same section, go to Repositories -> Repository URL, and paste "https://github.com/jmunozti/JenkinsAndTerraform.git"

4.- Save your configuration.

5.- Build your project. This build will ask you for your AWS_ACCESS_KEY_ID and your AWS_SECRET_ACCESS_KEY.

6.- Approve the Terraform Apply Stage .

7.- Review the created infraestructure.

8.- Approve the Terraform Destroy Stage .
