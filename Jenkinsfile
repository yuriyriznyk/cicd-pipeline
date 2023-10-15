pipeline {
    agent any
    stages {
        stage('code'){
            steps{
                git url: 'https://github.com/yuriyriznyk/cicd-pipeline.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh "scripts/build.sh"
            }
        }
        stage('Test') {
          steps {
            sh "scripts/test.sh"
          }
        }
        stage('Image build') {
          steps {
            sh "docker build -t yuriiriznyk/cicd-pipeline ."
            script {
              docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                docker.push('yuriiriznyk/cicd-pipeline')
              }
            }
          }
        }
    }
}
