pipeline {
  agent any
  stages
 {
  stage('Checkout')
  {
   steps { 
          git branch: 'master', url: 'https://github.com/katapeter/second.git'
       }
  }
  stage('PreCheck')
  {
  agent { label 'demo' }
   when { 
     anyOf {
           changeset "samplejar/**"
           changeset "samplewar/**"
     }
   }
   steps {
       script {
          env.BUILDME = "yes" // Set env variable to enable further Build Stages
       }
   }
  }
 stage('Build Artifacts')
  {
   agent { label 'demo' }
   when {environment name: 'BUILDME', value: 'yes'}
   steps { 
     
     script {
	    if (params.UNITTEST) {
		  unitstr = ""
		} else {
		  unitstr = "-Dmaven.test.skip=true"
		}
	
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
	
	
