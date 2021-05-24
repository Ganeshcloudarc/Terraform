pipeline {
  agent any
  
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
  tokenCredentialId: 'Slack-password')
  }
  }
  }
  }
  