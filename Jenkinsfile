pipeline {
    agent any 
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
    }
}
