pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arun-niko/node-ci-project'
            }
        }

        stage('Install Node') {
            steps {
                sh '''
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
    }

    post {
        success {
            echo "Node.js CI Pipeline completed successfully!"
        }
    }
}
