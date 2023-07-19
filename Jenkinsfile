pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('vismayamaliye')
    }
    stages { 

        stage('Build docker image') {
            steps {  
               zsh 'docker build -t vismayamaliye/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                zsh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                zsh 'docker push vismayamaliye/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
           zsh 'docker logout'
        }
    }
}
