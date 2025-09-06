pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }

        stage('Build & Test') {
            steps { sh 'echo "Simulating Build & Test..."' }
            post {
                always {
                    emailext(
                        to: 'your_email@gmail.com',
                        subject: "Build & Test Stage ${currentBuild.currentResult}: ${currentBuild.fullDisplayName}",
                        body: "The Build & Test stage finished with status: ${currentBuild.currentResult}.\nView logs at: ${env.BUILD_URL}",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps { sh 'echo "Simulating Security Scan..."' }
            post {
                always {
                    emailext(
                        to: 'your_email@gmail.com',
                        subject: "Security Scan Stage ${currentBuild.currentResult}: ${currentBuild.fullDisplayName}",
                        body: "The Security Scan stage finished with status: ${currentBuild.currentResult}.\nView logs at: ${env.BUILD_URL}",
                        attachLog: true
                    )
                }
            }
        }
    }

    post {
        success {
            emailext(
                to: 'your_email@gmail.com',
                subject: "SUCCESS: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job succeeded.\nCheck console: ${env.BUILD_URL}",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: 'your_email@gmail.com',
                subject: "FAILURE: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job failed. Check logs: ${env.BUILD_URL}",
                attachLog: true
            )
        }
    }
}
