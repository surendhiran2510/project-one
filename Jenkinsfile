pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git(url: 'https://github.com/surendhiran2510/project-one.git', branch: 'main')
            }
        }
        stage('DockerBuild') {
            steps {
                sh 'docker build -t notes-app .'
                sh 'docker tag notes-app surendhiran/notes-app:latest'
            }
        }
        stage('DockerPublish') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh 'docker login -u $USERNAME -p $PASSWORD'
                sh 'docker push surendhiran/notes-app:latest'
                }
            }
        }    
    }
}