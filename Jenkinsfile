pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
               git branch: 'main', url: ' git clone https://github.com/ganeshsaraf21/edureka-php-project.git'
            }
        }
        stage('Docker Build'){
            steps{
                sh "docker build . -t ganeshsaraf21/edureka-php-website"
            }
        }
        stage('DockerHub Push'){
            steps{

                withCredentials([string(credentialsId: 'dockerkey', variable: 'dockerkey')]) {
                      sh "docker login -u kaleemsony -p ${dockerkey}"
                }

                sh "docker push kaleemsony/my-php-website "
            }
        }
    }
}
