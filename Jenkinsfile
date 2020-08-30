pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -f dockerfile . -t 123123123123123456/jenkins_nodedev:v1.0'
            }
        }
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsid:"docker",usernamevariable:"USERNAME",passwordvariable:"Password")]){
                sh 'docker login --username $USERNAME --password $PASSWORD'
                sh 'docker push 123123123123123456/jenkins_nodedev:v1.0'
                }
            
            }
        }
        stage('Deploy') {
            steps {
               sh 'docker  run -d -p 4000:3000 123123123123123456/jenkins_nodedev:v1.0'
            }
        }
    }
