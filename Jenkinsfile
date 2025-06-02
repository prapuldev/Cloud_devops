pipeline {
    agent any

    environment {
        NODE_OPTIONS = '--openssl-legacy-provider'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }
    }

    post {
        success {
            echo "Deployment complete!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
