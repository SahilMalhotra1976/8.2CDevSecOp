pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') {
            steps {
                sh 'mvn clean test'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'echo "Running security scan..."'
                // Example: sh 'npm audit' or 'trivy fs .'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "Good news! The job succeeded.\nCheck console: ${env.BUILD_URL}",
                to: 'your_email@gmail.com'
            )
        }
        failure {
            emailext(
                subject: "FAILURE: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job failed. Please check logs here: ${env.BUILD_URL}",
                to: 'your_email@gmail.com'
            )
        }
    }
}
