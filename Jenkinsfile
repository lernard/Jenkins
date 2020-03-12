// Define variables
def serverip
def username = "ubuntu"

pipeline {
  agent any
  triggers { pollSCM('H/15 * * * *')}
  environment {
    sitename = "www.lernardtest.com"
  }
  parameters {
    choice(name: 'STRICTHOST', choices: ['No', 'Yes'], description: 'Strict host checking')
  }
  stages {
    stage ('Provision - Terraform') {
      steps {
        dir('Ansible') {
          git branch: 'master',
          credentialsId: 'a782029b-4767-494a-8a0b-fce90ae7df34',
          url: 'https://github.com/lernard/Ansible.git'
          sh """
            cd terraform_web_server/
            terraform init
            terraform apply -auto-approve
            """
          script {
              serverip = sh (
              script: 'aws ec2 describe-instances --filter "Name=tag:Name,Values=lernard_webserver" --query "Reservations[*].Instances[*].PublicIpAddress" --output=text',
              returnStdout: true
            ).trim()
          echo "The server IP is ${serverip}"
          }
        }
      }
    }
    stage ('Configure - Ansible') {
      steps {
        dir('Ansible') {
          sh """
            cd section6
            rm -f hosts
            echo "[web]\nweb1 ansible_host=${serverip}" > hosts
            while ! nc -z -w 5 ${serverip} 22; do echo "Waiting for server..."; sleep 5; done
            ansible-playbook -i hosts playbook_web.yml 
          """
        }
      }
    }
  }
}