// Define variables
def serverip = "3.84.143.200"
def username = "ubuntu"

pipeline {
  agent any
  environment {
    sitename = "www.lernardtest.com"
  }
  parameters {
    choice(name: 'STRICTHOST', choices: ['No', 'Yes'], description: 'Strict host checking')
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
        sh "scp -rv -o StrictHostKeyChecking=${params.STRICTHOST} -o UserKnownHostsFile=/dev/null build/* ${username}@${serverip}:/var/www/${sitename}/"
      }
    }
  }
}