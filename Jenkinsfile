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

        stage('Run Application') {
            steps {
                sh 'java -cp target/hello-world-maven-0.1.0.jar hello.HelloWorld'
            }
        }
    }

    post {
        success {
            echo ' Pipeline succeeded! Your "Hello World" app built and ran successfully.'
        }
        failure {
            echo ' Pipeline failed. Check the Console Output for details.'
        }
    }
}
