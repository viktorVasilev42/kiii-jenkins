pipeline {
  agent any
  stages {
    stage('Clone repository') {
      steps {
        checkout scm
      }
    }

    stage('Build image') {
      steps {
        script {
          app = docker.build("viktorvasilev42/kiii-jenkins")
        }

      }
    }

    stage('Push image') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
          }
        }

      }
    }

  }
}