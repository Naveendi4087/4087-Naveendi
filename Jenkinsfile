pipeline {
    agent any
    
    stages {
        stage('SCM Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Naveendi4087/4087-Naveendi.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app:${BUILD_NUMBER} .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 3000:3000 my-node-app:${BUILD_NUMBER}'
            }
        }
    }
}

