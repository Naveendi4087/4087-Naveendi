pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build the Docker image
                sh 'docker build -t my-node-app .'
            }
        }
        stage('Run') {
            steps {
                // Run the Docker container in detached mode (-d) and map port 3001 to 3000
                script {
                    dockerRunOutput = sh(script: 'docker run -d -p 3001:3000 my-node-app', returnStdout: true).trim()
                    dockerContainerId = dockerRunOutput.take(12)
                    echo "Container ID: ${dockerContainerId}"
                }
            }
        }
    }
    post {
        always {
            // Stop the Docker container using the container ID
            sh "docker stop ${dockerContainerId}"
        }
    }
}

