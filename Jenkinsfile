pipeline {
    agent {
        node {
            label node
        }
    }
    stages {
      stage('Git Checkout & Pulling latest code') {
          steps {
              script {
                  sh "ls"
              }
          }
      }
      
      stage('Deleting Images from Jenkins Slave Server') {
          steps {
              script {
                  sh "cd /home/ubuntu; ./docker-clean.sh"
              }
          }
      }
   }
}
