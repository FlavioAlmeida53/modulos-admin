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
				/* colocar os jobs do estágio de Build e testes unitários aqui */
			}
		}
		stage('Archiving Reports') {
			steps {
				/* colocar os jobs do estágio de arquivamento de relatórios aqui */
			}
		}
		stage('BDD tests job'){
			steps {
				/* colocar os jobs do estágio de execução de BDD aqui */
			}
		}
	}
	post {
		always {
			/* colocar as ações do bloco post aqui */
		}
	}
}
