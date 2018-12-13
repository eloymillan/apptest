pipeline {
    agent any

    stages {
        stage('PreBuild') {
            steps {
                echo 'Deleting current containers...'
                sh 'docker stop jenkins-docker-git||true'
                sh 'docker rm jenkins-docker-git||true'
                sh 'docker rmi jenkins-with-docker:testgit||true'
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
        stage('Deploy') {
            steps {
                echo 'Deploying.....'
                sh 'docker run -dit -v /var/run/docker.sock:/var/run/docker.sock --name jenkins-docker-git jenkins-with-docker:testgit'
                echo 'deployed'
            }
        }
        stage('Testing') {
            steps {
                echo 'Testing.....'
                sh 'docker exec -ti jenkins-docker-git pwd'
                echo 'Tested'
            }
        }
    }
}