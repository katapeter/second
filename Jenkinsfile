pipeline {
  agent any
  stages
 {
  stage('Checkout')
  {
       //agent { label 'demo' }
       steps { 
          git branch: 'master', url: 'https://github.com/katapeter/second.git'
       }
  }
 stage('PreCheck')
  {
  //agent { label 'demo' }
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
   //agent { label 'demo' }
   when {environment name: 'BUILDME', value: 'yes'}
   steps {
	   echo "hi"
   }
   }
 }
}	
