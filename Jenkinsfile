pipeline {
    agent none
    stages {
        stage('Check scm') {
            agent any
            steps {
                checkout scm
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'python:3.9-alpine'
                    args '-u="root"' 
                }
            }
            steps {
                sh 'pip install Flask xmlrunner'
                sh 'python3 test_app.py'
            }
        }
    }
    post {
        always {
            junit 'test-reports/*.xml'
        }
    }
}