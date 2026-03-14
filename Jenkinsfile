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
                sh 'cd ClientRoot && npx vite build'
            }
        }

        stage('Start Express Server') {
            steps {
                sh '''
                    pkill -f "node index.js" || true
                    cd Server
                    nohup node index.js > server.log 2>&1 &
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

