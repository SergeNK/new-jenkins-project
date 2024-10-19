pipeline {
    agent any

    environment {
        DB_HOST = '192.168.12.1'
        USERNAME = 'user1'
        PASSWORD = 'password123' 
    }

    parameters {
        string(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'Specify the env for deployment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: "Run Tests in pipeline")

    }
    stages {

        stage('test') {
            when {
                expression {
                    params.RUN_TESTS == true
                }
            }
            steps {
                echo "testing application"
            }
        }
        stage('Deploy') {
            steps {
                echo "deploying to ${params.ENVIRONMENT} environment"
            }
        }



        // stage('setup') {
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'server-creds',
        //         usernameVariable: "myuser", passwordVariable: "mypassword")]) {
        //             sh '''
        //             echo ${myuser}
        //             echo ${mypassword}
        //             '''
        //         }

        //         sh "pip install -r requirements.txt"
        //         echo "The Database IP is: ${DB_HOST}"
                
        //     }
        // }

        stage('Test') {
            steps {
                sh "python -m pytest"
                echo "The DB username: ${USERNAME} and the password is ${PASSWORD}"
                echo "Commit: ${env.GIT_COMMIT}"
            }
        }
    }
}