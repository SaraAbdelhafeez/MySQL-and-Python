pipeline {
    agent any
    stages {
        stage('build the images') {
            steps {
                sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/ecr:v$BUILD_NUMBER ./FlaskApp'
                // sh 'docker build -t 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:v$BUILD_NUMBER ./FlaskApp'
            }
        }
        stage('push the images') {
            steps {
                withCredentials([string(credentialsId: 'aws-Access-key-ID', variable: 'AWS_ACCESS_KEY_ID'), string(credentialsId: 'aws-Secret-access-key', variable: 'AWS_SECRET_ACCESS_KEY')]) {


                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/ecr:v$BUILD_NUMBER'
                    // sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:v$BUILD_NUMBER'
                }
            }
        }
    }
}