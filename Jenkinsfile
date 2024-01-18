pipeline {
    agent any
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/LondheShubham153/node-todo-cicd.git', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t rohithmarolix505069/anamika:latest'
            }
        }
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'anil', passwordVariable: 'anamika', usernameVariable: 'anamika')]) {
        	     sh "docker login -u ${env.anamika} -p ${env.anamika}"
                 sh 'docker push rohithmarolix505069/anamika:latest'
                }
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
