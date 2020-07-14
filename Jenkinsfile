pipeline{
	agent any
	
	stages {
		stage ('Checagem Git'){
		  steps('slave') {
		  deleteDir()
		  checkout scm
			}
		}
		stage ('Build Projeto'){
		  steps('slave') {
		  git credentialsId: 'github', url: 'https://github.com/FlavioAlmeida53/modulos-admin/tree/master/delivery-eureka-service/delivery-eureka-service'
		  sh 'mvn clean install'
		 cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: 'target/*.json', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1 
			}
		}
		
		
	}
}
