pipeline {
    agent any
    tools {
        maven 'maven-3.6.3'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'cd sprint1-jenkins-lab && mvn -B clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'cd sprint1-jenkins-lab && mvn -B test'
            }
            post {
                always {
                    junit 'sprint1-jenkins-lab/target/test-reports/*.xml'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'sprint1-jenkins-lab/target/*.jar', fingerprint: true
            }
        }
    }
}
