pipeline {
    agent any

   environment {
       APP_ENV = 'production'
   }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Create Virtual Environment') {
            steps {
                sh 'python3 -m venv venv'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Use Jenkins Credentials') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'lab3-secret',
                        variable: 'MY_SECRET'
                    )
                ]) {
                    sh 'echo "Secret is available to jenkins"'
                    sh 'echo "Environment: $APP_ENV"'
                }
            }
        }

        stage('Test') {
            steps {
                sh './venv/bin/python -m pytest'
            }
        }

        stage('Run Python') {
            steps {
                sh './venv/bin/python app.py'
            }
        }
    }

    post {
        success {
            echo 'All tests passed and Python program ran successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the test results.'
        }
    }
}
