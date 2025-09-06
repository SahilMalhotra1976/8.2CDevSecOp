pipeline {
    agent any

    stages {
        stage('Demo Build') {
            steps {
                echo 'This is a demo build.'
                echo 'Adding some console output to check attachment.'
            }
        }
    }

    post {
        always {
            emailext(
                from: 'malhotrasahil263@gmail.com',  // must match your Gmail account/app password
                to: 'malhotrasahil263@gmail.com',
                subject: "Jenkins Build ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: """Hello,

The build has finished. You can view the console output here: ${env.BUILD_URL}

Regards,
Jenkins""",
                attachLog: true
            )
        }
    }
}

