pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                echo 'Built'
            }
        }
        stage('Test') {
            steps {
                parallel(
                    'primero' : { echo "Testing..."
                    },
                    'segundo' : { echo "tested"
                    }
                )
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying.....';echo 'deployed'
                
            }
        }
    }
}