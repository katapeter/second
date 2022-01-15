pipeline {
    agent 'any'
    tools {
        jdk 'jdk1.8'
        maven 'maven3'
    }
    stages {
        stage('git pull'){
            steps{
                git 'https://github.com/katapeter/second.git'
            }
        }
         stage('mvn install'){
            steps{
                sh 'mvn clean'
                sh 'mvn install'
          }
       }
        stage('docker build'){
                steps{
                    sh 'docker --version'
                    sh 'docker build -t app:1 .'
                    sh 'docker tag app:1 katapeter/second'
                    sh 'docker push katapeter/second'
                     }
            }
    }
}
