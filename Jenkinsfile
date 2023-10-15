pipeline {
    agent any
    stages {
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
          }
        }
    }
}
