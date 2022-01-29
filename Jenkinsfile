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
 steps {
       script {
          env.BUILDME = "yes" // Set env variable to enable further Build Stages
       }
   }
  }
  stage('Build Artifacts')
  {
   when {environment name: 'BUILDME', value: 'yes'}
   steps {
     echo "Building Jar Component ..."
	dir ("./samplejar") {
	sh "mvn clean package"
		}

	echo "Building War Component ..."
	dir ("./samplewar") {
        sh "mvn clean package "
		  }
         
   }
  }
 }
}
	
	
