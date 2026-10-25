pipeline {
    agent any

    tools {
        maven '3.9.11'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/harbj3/midterm-spring-boot.git'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
                sh 'ls -lh target'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build successful! The fat jar is ready.'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
