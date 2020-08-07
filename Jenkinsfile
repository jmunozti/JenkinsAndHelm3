pipeline {
   agent any

  parameters {
    password (name: 'AWS_ACCESS_KEY_ID')
    password (name: 'AWS_SECRET_ACCESS_KEY')
  }
  environment {
    TF_WORKSPACE = 'default' //Sets the Terraform Workspace
    TF_IN_AUTOMATION = 'true'
    AWS_ACCESS_KEY_ID = "${params.AWS_ACCESS_KEY_ID}"
    AWS_SECRET_ACCESS_KEY = "${params.AWS_SECRET_ACCESS_KEY}"
  }
   stages {
      stage('Source') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/jmunozti/terraform.git'
         }
      }

      stage('Terraform Init') {
        steps {
            sh "cd terraform && terraform init -input=false"
        }
      }
      stage('Terraform Plan') {
            steps {
              sh "cd terraform && terraform plan -out=tfplan -input=false"
            }
          }
      stage('Terraform Apply') {
        steps {
          input 'Apply Plan'
          sh " cd terraform && terraform apply -input=false tfplan"
        }
      }
      stage('Terraform Destroy') {
        steps {
          input 'Destroy'
          sh " cd terraform && terraform  destroy -input=false -auto-approve"
        }
      }

   }
   post {
            always {
                echo 'This will always run'
            }
            success {
                mail bcc: '', body: "<b>SUCCESS</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "SUCCESS CI: Project name -> ${env.JOB_NAME}", to: "jmunozti@gmail.com";
            }
            failure {
                mail bcc: '', body: "<b>ERROR</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "jmunozti@gmail.com";
            }
            unstable {
                echo 'This will run only if the run was marked as unstable'
            }
            changed {
                echo 'This will run only if the state of the Pipeline has changed'
            }
        }

}
