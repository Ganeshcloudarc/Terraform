pipeline {
  agent any
  environment {
    AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-access-key-id')
    AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
}
  
  tools {
    terraform 'terraform'
  }

stages{
  stage('terraform init'){
    steps{
       sh 'terraform init'
       sh 'terraform apply -auto-approve'
    }
  }
  stage('jenkins build alerts'){
   steps{
  slackSend(channel: '#jenkins-deployments', color: '#009933', message: 'job1 build sucessful', teamDomain: 'jenkins-slack',
  tokenCredentialId: 'slack-passwd')
  }
  }
  }
  }
  