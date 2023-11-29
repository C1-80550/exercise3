pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80550/exercise3.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    sh 'echo dckr_pat_JLlxnh6GrET6t602Z9BMo-t1jt0 | docker login -u yogesh9221 --password-stdin'
                    sh 'docker build -t yogesh9221/mywebsite .'
                    sh 'docker image push yogesh9221/mywebsite'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl -- apply -f myservice.yaml'
                }
            }
        }                
            
        
    }

