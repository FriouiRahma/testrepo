pipeline {
    agent any
     environment {
             DOCKERHUB_CREDENTIALS = credentials('docker')
             scannerHome = tool 'SonarQube'
        }
    stages {
        stage('Building docker image client') {
            steps {
                dir("server/"){
                    bat "docker build -t $DOCKERHUB_CREDENTIALS_USR/express-app ."
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          bat "docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW"
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                bat "docker push $DOCKERHUB_CREDENTIALS_USR/express-app"
      }
    }

  //  stage('SonarQube analysis') {
  //           steps {
  //                 dir("client/"){
  //                   bat "npm i sonarqube-scanner"
  //                   bat "npm run sonar"
  //                 }
  //           }
  //       }
    }
}
