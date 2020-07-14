def COLOR_MAP = ['SUCCESS': 'good', 'FAILURE': 'danger', 'UNSTABLE': 'danger', 'ABORTED': 'danger']
pipeline{
	agent {
		docker {
			image 'maven'
			args '-v /root/.m2:/root/.m2'
		}
	}
	stages {
		stage('Checkout') {
			steps {
				/* colocar os jobs do estágio de Checkout aqui */
				slackSend channel: 'jenkins-ci', color: '#33AFFF', message: "*STARTED*: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'\n *More info at:* ${env.BUILD_URL}", teamDomain: 'devteam', tokenCredentialId: 'slack'
      git branch: 'dev', credentialsId: 'github', url: 'https://github.com/FlavioAlmeida53/projetoJucesp'
			}
		}
		stage('Build + Unit tests') {
			steps {
			   sh 'mvn clean test'"
			}
		}
		stage('Archiving Reports') {
		steps {
			dir(path: '.') {
			    publishHTML([allowMissing: true, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'target/site/jacoco/', reportFiles: 'index.html', reportName: 'Code Coverage', reportTitles: 'Code Coverage'])
			    step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/TEST-*.xml'])
			}
		}
		stage('BDD tests job'){
			 steps {
				git credentialsId: 'github', url: 'https://github.com/murillowelsi/repos/bdd-tests'
				sh 'mvn clean install'
				cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: 'target/*.json', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1                       
			    }
		}
	}
	post {
		always {
			slackSend channel: 'jenkins-ci', teamDomain: 'devteam', tokenCredentialId: 'slack',
			    color: COLOR_MAP[currentBuild.currentResult],
			    message: "*${currentBuild.currentResult}:* Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'\n *More info at:* ${env.BUILD_URL}"
		    }
	}
}
