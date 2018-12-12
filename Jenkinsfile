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
                    'primero' : { echo "Primero Tested"
                    },
                    'segundo' : { echo "Segundo tested"
                    },
                    'tercero' : { echo "Tercero tested"
                    },
                    'cuarto' : { echo "Cuarto tested"
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