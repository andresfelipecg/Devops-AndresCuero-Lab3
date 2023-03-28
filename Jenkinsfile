pipeline {
    agent any
    tools {
        maven 'maventool' // Name of the Maven tool as defined in Jenkins
    }
    environment {
         DOCKERHUB_CREDENTIALS_USR = credentials('my-docker-creds').username
         DOCKERHUB_CREDENTIALS_PSW = credentials('my-docker-creds').password
    }
    stages {
        stage('Check out') {
            steps {
                git branch: 'main', url: 'https://github.com/andresfelipecg/Devops-AndresCuero-Lab3'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Docker Build') {
            steps {
                bat 'docker build -t andresfelipecg/mavenproject:dockerfileimage .'
            }
        }
        stage('Docker Login') {
            steps {
                bat 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
            }
        }
        stage('Docker Push') {
            steps {
                bat 'docker push andresfelipecg/mavenproject:dockerfileimage'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}
