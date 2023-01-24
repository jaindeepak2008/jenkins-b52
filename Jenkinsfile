pipeline {
    agent any

    environment {                           // Declaring at Pipeline will allow all the stages to access this variable
        ENV_URL  = "pipeline.global.com"
        SSH_CRED = credentials('SSH_CRED') 
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '3'))
        disableConcurrentBuilds()
        disableResume()
        timeout(time: 1, unit: 'MINUTES')
    }

    stages {
        stage('One') {
            steps {
                echo "I am stage One"
                echo "Env URL is ${ENV_URL}"
                sleep 300
            }
        }

        stage('Two') {
            environment {                           // Declaring at stage will allow only that stages to access that variable
                ENV_URL = "stage2.global.com"
            }
            steps {
                echo "I am stage Two"
                echo "Env URL is ${ENV_URL}"
            }
        }

        stage('Three') {
            steps {
                sh '''
                    echo hello World
                    echo Hai World
                    echo I am using Pipeline Syntax Generator
                    env
                '''
            }
        }

    }
}