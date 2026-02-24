pipeline {
    agent any

    environment {
        DOCKER_HUB = "ramashashank"
        BACKEND_IMAGE = "mean-backend"
        FRONTEND_IMAGE = "mean-frontend"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/ramashashank2003/assignment_crud-dd-task-mean-app.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'docker build -t $DOCKER_HUB/$BACKEND_IMAGE:latest ./backend'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t $DOCKER_HUB/$FRONTEND_IMAGE:latest ./frontend'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-hub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Images') {
            steps {
                sh 'docker push $DOCKER_HUB/$BACKEND_IMAGE:latest'
                sh 'docker push $DOCKER_HUB/$FRONTEND_IMAGE:latest'
            }
        }

        stage('Deploy on EC2') {
            steps {
                sh '''
                docker compose down || true
                docker compose pull
                docker compose up -d
                '''
            }
        }
    }
}
