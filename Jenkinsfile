pipeline {
    environment{
        branchName="viktorvasilev42/kiii-jenkins"
    }
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
                    // right parameter is jenkins credentials
                   docker.withRegistry('https://registry.hub.docker.com', 'vv-dockerhub') {
                       app.push("latest")  
                   }
                }
            }
        }
    }
}
