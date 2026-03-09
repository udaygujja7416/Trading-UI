pipeline {

    agent any

    environment {
        SKIP_PREFLIGHT_CHECK = 'true'
    }

    stages {

        stage('Git Checkout') {
            steps {
                git 'https://github.com/betawins/Trading-UI.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
                sh 'npm audit fix || true'
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
                npm install -g pm2
                pm2 stop Trading-UI || true
                pm2 delete Trading-UI || true
                pm2 start npm --name "Trading-UI" -- start
                '''
            }
        }

    }
}
