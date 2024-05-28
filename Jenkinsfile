pipeline {
    agent any
    environment {
        SSH_CRED = credentials('webkey')
    }
    stages {
        
        stage('Build') {
            steps {
                echo 'packaging app'
                sh "pwd"
                sh "ls"
            } 
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }


        stage('Clean-Up') {
            steps {
                echo 'Remove existing files'
            }
        }
    }
}
