pipeline {
    agent any

    tools {
        nodejs "NodeJS 18"
    }

    environment {
        BUILD_DIR = 'build'
        REMOTE_USER = 'ubuntu'
        REMOTE_HOST = '172.31.19.76'
        REMOTE_PATH = '/home/ubuntu/Cloud_devops'  // Your actual Nginx project path
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/prapuldev/Cloud_devops.git'
            }
        }

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

        stage('Deploy using rsync') {
            steps {
                sh """
                rsync -avz -e "ssh -o StrictHostKeyChecking=no" $BUILD_DIR/ $REMOTE_USER@$REMOTE_HOST:$REMOTE_PATH/
                """
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
