pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'cd starter && mvn -B clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'cd starter && mvn -B test'
            }
            post {
                always {
                    junit 'starter/target/test-reports/*.xml'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'starter/target/*.jar', fingerprint: true
            }
        }
    }
}
