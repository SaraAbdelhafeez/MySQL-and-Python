pipeline {
    agent any
    stages {
        stage('build the images') {
            steps {
                sh 'docker build -t flask-app:v$BUILD_NUMBER ./FlaskApp'
                sh 'docker build -t mysql-db:v$BUILD_NUMBER ./FlaskApp'
            }
        }
        stage('push the images') {
            steps {
                withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {

                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/flask-app:v$BUILD_NUMBER'
                    sh 'docker push 524041749761.dkr.ecr.us-east-1.amazonaws.com/mysql-db:v$BUILD_NUMBER'
                }
            }
        }
    }
}