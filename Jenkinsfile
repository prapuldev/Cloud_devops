pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {

        stage('Clone Repository') {
            steps {
                // Make sure this repo is public or Jenkins has credentials set up
                git 'https://github.com/prapuldev/Cloud_devops.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Assumes package.json is in the root of the cloned repo
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
            echo "✅ Deployment complete!"
        }
        failure {
            echo "❌ Deployment failed!"
        }
    }
}
