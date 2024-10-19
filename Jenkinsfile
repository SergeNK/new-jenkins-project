pipeline {
    agent any
    stages {

        stage('checkout') {
            steps {
                git url: 'https://github.com/SergeNK/new-jenkins-project.git', branch: 'main'
                sh "ls -ltr"
            }
        }

        stage('setup') {
            steps {
                sh "pip install -r requirements.txt"
            }
        }

        stage('Test') {
            steps {
                sh "python -m pytest"
            }
        }
    }
}