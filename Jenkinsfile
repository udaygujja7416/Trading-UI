pipeline {

    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git 'https://github.com/betawins/Trading-UI.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm audit fix'
                sh 'npm install'
            }
        }

        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Start Application') {
            steps {
                sh '''
                cd build
                pm2 --name Trading-UI start npm -- start
                '''
            }
        }

    }
}
