pipeline {
    agent any

    environment {
        DB_HOST = '192.168.12.1'
        USERNAME = 'user1'
        PASSWORD = 'password123'
        SERVER_CREDS = credentials('server-creds')
    }
    stages {

        // stage('checkout') {
        //     steps {
        //         git url: 'https://github.com/SergeNK/new-jenkins-project.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }

        stage('setup') {
            steps {
                sh "pip install -r requirements.txt"
                echo "The Database IP is: ${DB_HOST}"
                sh 'echo "my creds username: ${SERVER_CREDS_USR}"'
                sh 'echo "my creds password: ${SERVER_CREDS_PSW}"'
                
            }
        }

        stage('Test') {
            steps {
                sh "python -m pytest"
                echo "The DB username: ${USERNAME} and the password is ${PASSWORD}"
                echo "Commit: ${env.GIT_COMMIT}"
            }
        }
    }
}