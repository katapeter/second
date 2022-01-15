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
    }
}
