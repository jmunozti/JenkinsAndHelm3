# JenkinsAndTerraform

This is a Jenkins Pipeline to deploy AWS resources using Terraform.

# Usage

1.- Run Jenkins.

2.- Create a new Jenkins Pipeline.

3.- Configure your pipeline.

Go to Configure -> Pipeline -> Definition and choose "Pipeline script form SCM".

In the same section, go to SCM and choose "Git"

In the same section, go to Repositories -> Repository URL, and paste "https://github.com/jmunozti/JenkinsAndTerraform.git"

4.- Save your configuration.

5.- Build your project. This build will ask you for your AWS_ACCESS_KEY_ID and your AWS_SECRET_ACCESS_KEY.

6.- Enjoy!!
