pipeline {
    agent any
    stages {
        stage('build the images') {
            steps {
                sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app:v$BUILD_NUMBER ./FlaskApp'
                sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:v$BUILD_NUMBER ./FlaskApp'
            }
        }
        stage('push the images') {
            steps {
                withCredentials([string(credentialsId: 'aws-ecr-token', variable: 'AWS_ECR_TOKEN')]) {


                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app:v$BUILD_NUMBER'
                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:v$BUILD_NUMBER'
                }
            }
        }
    }
}