pipeline {
  agent any

  stages {

    stage('Checkout') {
      steps {
        checkout scm
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
      echo 'Python program failed.'
    }
  }
}
