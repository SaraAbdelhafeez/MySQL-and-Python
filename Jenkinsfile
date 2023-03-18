pipeline {
    agent any
    stages {
        stage('aws erc login') {
            steps {
                withCredentials([string(credentialsId: 'Access-key-ID', variable: 'AWS_ACCESS_KEY_ID'), string(credentialsId: 'Secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')]) {
                    sh 'aws ecr get-login-password | docker login --username AWS --password-stdin 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app'
                    sh 'aws ecr get-login-password | docker login --username AWS --password-stdin 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db'
                }
            }
        }
        stage('build the images') {
            steps {
                sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app:latest ./FlaskApp'
                sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:latest ./MySQL_Queries'
            }
        }
        stage('push the images') {
            steps {
                withCredentials([string(credentialsId: 'Access-key-ID', variable: 'AWS_ACCESS_KEY_ID'), string(credentialsId: 'Secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')]) {
                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app:latest'
                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:latest'
                    sh 'echo "build is done!"'
                  
                }
            }
        }
    }
}
