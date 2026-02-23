pipeline {
    agent {
        node {
            label 'master'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arun-niko/node-ci-project'
            }
        }

        stage('Install Node') {
            steps {
                sh '''
                echo "Installing Node.js..."
                sudo apt update
                sudo apt install -y nodejs npm
                node -v
                npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo "Build completed."
            }
        }
    }

    post {
        success {
            echo "Node.js CI Pipeline completed successfully!"
        }
        failure {
            echo "Node.js CI Pipeline failed!"
        }
    }
}

