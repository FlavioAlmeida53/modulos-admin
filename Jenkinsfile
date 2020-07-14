pipeline{
	agent any
	
	stages {
		stage('Teste no Git'){
			steps{
				echo "Copiando arquivos do Git"
			}
		}
	}
	stages {	
				stage('Download das Libs'){
					steps{ echo "Libs do projeto" }
				}
				stage('Gerando o Package'){
					steps{ echo "Package do projeto" }
				}
				stage('Gerar Jar'){
					steps{ echo "Compile do projeto" }
				}
			}
	stages {	
				stage('Parando sistema'){
					steps{
						  echo "Sistema Pusado"
					}
				}
				stage('Copiando Jar para o diretório'){
					steps{
						  echo "Sistema sendo copiado para paste dev"
					}
				}
				stage('Start da aplicação em dev'){
					steps{
						  echo "Sistema sendo executado em dev"
					}
				}
		}
		stages {
				stage('Parando sistema'){
					steps{
						  echo "Sistema Pusado"
					}
				}
				stage('Copiando Jar para o diretório'){
					steps{
						  echo "Sistema sendo copiado para paste Hom"
					}
				}
				stage('Start da aplicação em Hom'){
					steps{
						  echo "Sistema sendo executado em hom"
					}
				}
			}
}
