pipeline{
    agent any
    stages{
        stage('Git clone'){
            steps{
                git 'https://github.com/udaykg19/HelloWorld-Springboot-App.git'
            }
        }
        
        stage('maven build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Create Dockerimage'){
            steps{
                sh 'docker build -t udaykg:latest .'
                 sh 'docker login -u ${DockerHubCredentials.username} -p ${DockerHubCredentials.password}'
                sh 'docker push udaykg'
                
            }
        }
        
    }
}
