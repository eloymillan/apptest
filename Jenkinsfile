pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
            steps {
                echo 'Built'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                echo 'Tested'
            }
        }
        stage('Deploy') {
            steps {
                sh echo 'Deploying.....'&&echo 'Deployed'
            }
        }
    }
}