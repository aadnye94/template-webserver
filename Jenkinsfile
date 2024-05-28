pipeline {
    agent any
    environment {
        SSH_CRED = credentials('webkey')
    }
    stages {
        
        stage('Build') {
            steps {
                echo 'packaging app'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying'
                sh "pwd"
                sh "ls"
            }
        }


        stage('Clean-Up') {
            steps {
                echo 'Remove existing files'
            }
        }
    }
}
