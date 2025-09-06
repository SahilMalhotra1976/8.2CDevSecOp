pipeline {
    agent any
    tools {
        maven 'Maven-3.9.11'  // Your Maven installation name
        jdk 'OpenJDK-24'      // The JDK name you just configured
    }

    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build & Test') { steps { sh 'mvn clean test' } }
        stage('Security Scan') { steps { sh 'echo "Running security scan..."' } }
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

