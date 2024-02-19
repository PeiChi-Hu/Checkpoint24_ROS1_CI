pipeline {
    agent any
    stages {
        stage('Install Docker') {
            steps {
                script {
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y docker.io docker-compose'
                    sh 'sudo service docker start'
                    sh 'sudo usermod -aG docker $USER'
                    sh 'newgrp docker'
                    sh 'sudo service docker status'
                    sh 'sudo docker ps -a'
                    sh 'sudo service docker restart'
                }
            }
        }
        stage('Build Dockerfile') {
            steps {
                script {
                    dir('/home/user/catkin_ws/src/ros1_ci') {
                        sh 'sudo docker build -t leokim10073-cp24:ros1 .'
                    }
                }
            }
        }
        stage('Run Docker Compose') {
            steps {
                script {
                    dir('/home/user/catkin_ws/src/ros1_ci') {
                        sh 'sudo docker-compose up'
                    }
                }
            }
        }
    }
}