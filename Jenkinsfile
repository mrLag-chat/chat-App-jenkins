pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {

        stage('Install Backend Dependencies') {
            steps {
                sh 'cd Server && npm install'
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                sh 'cd ClientRoot && npm install'
            }
        }

        stage('Build React (Vite) App') {
            steps {
                sh 'cd ClientRoot && npm run build'
            }
        }

        stage('Restart Express with PM2') {
            steps {
                sh '''
                    cd Server
                    pm2 describe express-app > /dev/null 2>&1 \
                        && pm2 restart express-app \
                        || pm2 start index.js --name express-app
                    pm2 save
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed! Check logs.'
        }
    }
}