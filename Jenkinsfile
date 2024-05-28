pipeline {
    agent any
    environment {
        SSH_CRED = credentials('webkey')
        def CONNECT = 'ssh -o StrictHostKeyChecking=no ubuntu@ec2-3-96-178-26.ca-central-1.compute.amazonaws.com'
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
                sh "zip -r webapp.zip ."
                sh "ls"
            }
        }

  stage('Deploy') {
            steps {
                echo 'Deploying'
               sshagent(['webkey']) {
                    sh 'scp -o StrictHostKeyChecking=no -i $SSH_CRED webapp.zip ubuntu@ec2-3-96-178-26.ca-central-1.compute.amazonaws.com:/home/ubuntu'
                    sh '$CONNECT "sudo apt install zip -y"'
                    sh '$CONNECT "sudo rm -rf /var/www/html/"'
                    sh '$CONNECT "sudo mkdir /var/www/html/"'
                    sh '$CONNECT "sudo unzip webapp.zip -d /var/www/html/"'    
                }
            }
        }


        stage('Clean-Up') {
            steps {
                echo 'Remove existing files'
                sshagent(['web-server-key']) {
                    sh '$CONNECT "sudo rm /home/ubuntu/webapp.zip"'
                }
                sh "rm webapp.zip"
            }
        }
    }
}
