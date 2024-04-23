pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -p 3002:3000 my-node-app'
            }
        }
    }
}
