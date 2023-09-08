pipeline {
    agent any
    environment {
        DOCKER_HUB_USERNAME = credentials('DockerHubCredentials').username
        DOCKER_HUB_PASSWORD = credentials('DockerHubCredentials').password
    }
    stages {
        stage('Git clone') {
            steps {
                git 'https://github.com/udaykg19/HelloWorld-Springboot-App.git'
            }
        }
        stage('Maven build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Create Docker image') {
            steps {
                sh 'docker build -t udaykg:latest .'
                sh "docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD"
                sh 'docker push udaykg:latest'
            }
        }
    }
}
