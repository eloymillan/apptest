pipeline {
    agent any

    stages {
        stage('PreBuild') {
            steps {
                echo 'Deleting current containers...'
                sh 'docker stop jenkins-docker-git||true'
                sh 'docker rm jenkins-docker-git||true'
                sh 'docker rmi jenkins-with-docker:testgit||true'
                sh 'docker rm apptest_apache_1 apptest_mysql_1 apptest_php_1||true'
                echo 'Deleted'
            }
        }
        stage('Build Docker image') {
            steps {
                echo "Creating Image..."
                sh 'docker build -t jenkins-with-docker:testgit .'
                echo "Created Image"
            }
        }
        stage('Deploy container') {
            steps {
                echo 'Deploying.....'
                sh 'docker run -dit -v /var/run/docker.sock:/var/run/docker.sock --name jenkins-docker-git jenkins-with-docker:testgit'
                echo 'deployed'
            }
        }
        stage('Deploy Docker-Compose') {
            steps {
                echo 'Deploying.....'
                sh 'docker-compose up -d'
                echo 'deployed'
            }
        }
        stage('Testing') {
            steps {
                echo 'Testing.....'
                sh 'docker exec jenkins-docker-git pwd'
                echo 'Tested'
            }
        }
    }
}