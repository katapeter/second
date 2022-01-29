pipeline {
  agent any
  stages
 {
  stage('Checkout')
  {
    //agent { label 'Dev' }
    steps { 
          git branch: 'master', url: 'https://github.com/katapeter/second.git'
       }
  }
 stage('PreCheck')
  {
  //agent { label 'Dev' }
 steps {
       script {
          env.BUILDME = "yes" // Set env variable to enable further Build Stages
       }
   }
  }
  stage('Build Artifacts')
  {
   //agent { label 'Dev' }
   when {environment name: 'BUILDME', value: 'yes'}
   steps {
     echo "Building Jar Component ..."
	dir ("./samplejar") {
	sh "mvn clean package ${unitstr}"
		}

	echo "Building War Component ..."
	dir ("./samplewar") {
        sh "mvn clean package "
		}
          }
   }
 }
}
}	
	
