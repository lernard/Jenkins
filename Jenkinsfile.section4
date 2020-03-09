pipeline {
  agent any
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
        sh 'scp -rv -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null /var/lib/jenkins/workspace/Section4_master/build/* ubuntu@3.84.143.200:/var/www/www.lernardtest.com/'
      }
    }
  }
}