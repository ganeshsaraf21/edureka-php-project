pipeline {
    agent {
        label 'slave_1'
    }
    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/ganeshsaraf21/edureka-php-project.git'
            }
        }
        stage('Docker Build'){
            steps{
                sh "docker build . -t ganeshsaraf21/edureka-php-website"
            }
        }
        stage('Docker Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerkey', variable: 'dockerkey')]) {
                      sh "docker login -u ganeshsaraf21 -p ${dockerkey}"
                }
                sh "docker push ganeshsaraf21/edureka-php-website"
            }
        }
        stage('Docker run container'){
            steps{
                sh "docker container run -dt --name php_website8 -p 9086:80 ganeshsaraf21/edureka-php-website"
            }
        }
    }
}
