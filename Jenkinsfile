pipeline {
    agent any
    tools {
        maven 'maventool' // Name of the Maven tool as defined in Jenkins
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}