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
				echo "Sistema sendo copiado para paste dev"
			}
		}
		stage('Archiving Reports') {
			steps {
				echo "Sistema sendo copiado para paste dev"
			}
		}
		stage('BDD tests job'){
			steps {
				echo "Sistema sendo copiado para paste dev"
			}
		}
	}
	post {
		always {
			
		}
	}
}
