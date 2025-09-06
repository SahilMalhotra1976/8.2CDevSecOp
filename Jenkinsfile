pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }

        stage('Build & Test') {
            steps { sh 'echo "Simulating Build & Test..."' }
        }

        stage('Security Scan') {
            steps { sh 'echo "Simulating Security Scan..."' }
        }
    }

    post {
        success {
            emailext(
                to: 'malhotrasahil263@gmail.com',
                subject: "SUCCESS: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job succeeded.\nCheck console: ${env.BUILD_URL}",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: 'malhotrasahil263@gmail.com',
                subject: "FAILURE: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job failed. Check logs: ${env.BUILD_URL}",
                attachLog: true
            )
        }
    }
}

    
