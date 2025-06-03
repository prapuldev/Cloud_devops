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

        stage('Deploy to Nginx Server') {
            steps {
                // Copy build files to nginx server using scp
                sh '''
                    scp -i /home/ubuntu/ssh-keys/key.pem -r build/* ubuntu@172.31.29.37:/var/www/html/
                '''
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
