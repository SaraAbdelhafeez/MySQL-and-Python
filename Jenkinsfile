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
                docker.withRegistry(
                    'https://524041749761.dkr.ecr.us-east-1.amazonaws.com/ecr',
                    'ecr:ecr:AKIAXUA2SQUAYH2SXYUD'
                ) {
                    def appImage = docker.build('ecr')
                    def dbImage = docker.build('ecr')
                    appImage.push('flask-app:v$BUILD_NUMBER')
                    dbImage.push('mysql-db:v$BUILD_NUMBER')
                }
            }
        }
    }
}