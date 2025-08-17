pipeline {
  agent any

  tools {
    maven 'Maven 3.8.7'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build & Package') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Test (optional)') {
      when {
        expression { fileExists('src/test/java') }
      }
      steps {
        sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
  }

  post {
    success {
      echo 'Build completed successfully!'
    }
    failure {
      echo 'Build failed. Check the logs.'
    }
  }
}
