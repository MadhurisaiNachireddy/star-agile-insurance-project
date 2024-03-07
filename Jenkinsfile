pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-mad')
    }
   stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/MadhurisaiNachireddy/star-agile-insurance-project.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Build docker image') {
            steps {  
                sh 'docker build -t insure .'
                sh 'docker tag insure:latest madhurisai12/insurance14:latest'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
    stage('push image') {
            steps{
                sh 'docker push madhurisai12/insurance124:latest'
               }
          }
   
 stage('Deploy') {
            steps{
                   sh 'docker run -itd --name demo2 -p 8090:8090 madhurisai12/insurance124:latest'
                 }
          }   
}
       post {
            always {
               sh 'docker logout'
        }
    }
}
