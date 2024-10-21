pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/johnzama/interactive-cv'
            }
        }
        
        stage('Build') {
            steps {
                // Build the Docker image
                sh 'docker build -t interactive-cv .'
            }
        }
        
        stage('Test') {
            steps {
                // Optionally, you can add test commands here if you have tests
                echo 'Testing the application...'
            }
        }
        
        stage('Deploy') {
            steps {
                // Run the Docker container
                sh 'docker run -d -p 8080:80 --name interactive-cv interactive-cv'
            }
        }
    }
    
    post {
        always {
            // Cleanup Docker containers and images after build
            sh 'docker rm -f interactive-cv || true'
            sh 'docker rmi interactive-cv || true'
        }
    }
}

