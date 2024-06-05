pipeline {
    agent {
        node{
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.7/bin:$PATH"
}
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    stage('SonarQube analysis'){
        environment{
            scannerHome = tool 'sonar-scanner'
        }
        steps{

        withsonarQubeEnv('valaxy-sonarqube-server') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        }
        }
    }
    }
