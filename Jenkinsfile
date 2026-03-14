pipeline {
    agent any

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

        stage('Build React App') {
            steps {
                sh 'cd ClientRoot && npm run build'
            }
        }

    }
}