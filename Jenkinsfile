pipeline {
  agent any

  stages {

    stage('Checkout') {
      steps {
        checkout scm
      }
    }

  stage('Install Dependencies') {
    steps {
      sh 'python3 -m pip install -r requirements.txt'
    }
  }

  stage('Test') {
    steps {
      sh 'python3 -m pytest'
    }
  }
        
  stage('Run Python') {
    steps {
      sh 'python3 app.py'
    }
  }
}

  post {
    success {
      echo 'Python program ran successfully!'
    }

    failure {
      echo 'Pipeline failed. Check the test results.'
    }
  }
}
