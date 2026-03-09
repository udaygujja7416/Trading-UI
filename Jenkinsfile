pipeline {
    agent any

    tools {
        nodejs 'NodeJS18'
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('Build Application') {
            steps {
                sh 'npm run build || true'
            }
        }

    }
}
