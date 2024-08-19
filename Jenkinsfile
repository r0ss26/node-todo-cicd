// pipeline {
//     agent { label 'node-agent' }
    
//     stages{
//         stage('Code'){
//             steps{
//                 git url: 'https://github.com/LondheShubham153/node-todo-cicd.git', branch: 'master' 
//             }
//         }
//         stage('Build and Test'){
//             steps{
//                 sh 'docker build . -t trainwithshubham/node-todo-test:latest'
//             }
//         }
//         stage('Push'){
//             steps{
//                 withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
//         	     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
//                  sh 'docker push trainwithshubham/node-todo-test:latest'
//                 }
//             }
//         }
//         stage('Deploy'){
//             steps{
//                 sh "docker-compose down && docker-compose up -d"
//             }
//         }
//     }
// }

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh "docker stop node-todo-app || true"
                sh "docker rm node-todo-app || true"
                sh "docker build . -t todo-node-app"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh "docker run -d --name node-todo-app -p 8000:8000 todo-node-app"
            }
        }
    }
}
