pipeline {
    agent any

    tools {
        maven 'Maven-3.9.11' // matches the name you set in Jenkins
    }

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
            post {
                always {
                    emailext(
                        to: 'your_email@gmail.com',
                        subject: "Test Stage ${currentBuild.currentResult}: ${currentBuild.fullDisplayName}",
                        body: "The Test stage finished with status: ${currentBuild.currentResult}.\nView logs at: ${env.BUILD_URL}",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                sh 'echo "Running security scan..."'
                // Replace with actual security scan command, e.g., `sh "trivy fs ."`
            }
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
                body: "Good news! The job succeeded.\nCheck console: ${env.BUILD_URL}",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: 'your_email@gmail.com',
                subject: "FAILURE: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The job failed. Please check logs here: ${env.BUILD_URL}",
                attachLog: true
            )
        }
    }
}

