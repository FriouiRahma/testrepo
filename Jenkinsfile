pipeline {
    agent any
     environment {
             DOCKERHUB_CREDENTIALS = credentials('docker')
        }
    stages {
        stage('Building docker image client') {
            steps {
                dir("client/"){
                    bat 'docker build -t rahmafrioui/client .'
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                sh 'docker push $DOCKER_CREDS_USR/client'
      }
    }
    }
}
