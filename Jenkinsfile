pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/mrLag-chat/Chat-Appv1.git'
            }
        }

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

        stage('Build React App') {
            steps {
                sh 'cd ClientRoot && npm run build'
            }
        }

    }
}