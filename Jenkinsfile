// Define variables
def serverip = "3.84.143.200"
def username = "ubuntu"

pipeline {
  agent any
  environment {
    sitename = "www.lernardtest.com"
  }
  stages {
    stage('Clone Git') {
      steps {
        checkout scm
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Deploy') {
      when {branch 'master'}
      steps {
        sh "scp -rv -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null build/* ${username}@${serverip}:/var/www/${sitename}/"
      }
    }
  }
}