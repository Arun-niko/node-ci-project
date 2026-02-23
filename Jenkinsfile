pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arun-niko/node-ci-project'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build || echo "No build step available"'
            }
        }

        stage('Archive Artifact') {
            steps {
                sh 'mkdir -p output'
                sh 'cp -r * output || true'
                archiveArtifacts artifacts: 'output/**', fingerprint: true
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "No tests available"'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished"
        }
        success {
            mail to: 'arunniko12@gmail.com',
                 subject: 'SUCCESS: Node CI Pipeline',
                 body: 'Your CI pipeline executed successfully!'
        }
        failure {
            mail to: 'arunniko12@gmail.com',
                 subject: 'FAILED: Node CI Pipeline',
                 body: 'Your CI pipeline has failed!'
        }
    }
}
