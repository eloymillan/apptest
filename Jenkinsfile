pipeline {
    agent any

    stages {
        stage('PreBuild') {
            steps {
                echo 'Deleting current containers...'
                docker stop jenkins-docker-git
                docker rm jenkins-docker-git
                docker rmi 'jenkins-with-docker:testgit'
                echo 'Deleted'
            }
        }
        stage('Build Docker image') {
            steps {
                echo "Creating Image..."
                docker build -t 'jenkins-with-docker:testgit' .
                echo "Created Image"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying.....'
                docker run -dit -v '/var/run/docker.sock:/var/run/docker.sock' --name jenkins-docker-git 'jenkins-with-docker:testgit'
                echo 'deployed'
            }
        }
        stage('Testing') {
            steps {
                echo 'Testing.....'
                docker exec -ti jenkins-docker-git pwd
                echo 'Tested'
            }
        }
    }
}