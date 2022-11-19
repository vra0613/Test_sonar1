pipeline {
	agent {label 'java1'}
  tools{
    maven 'local_maven'
     }
		stages {
			stage ('BUILD') {
				steps {
					sh 'mvn clean package'
				}		
			
			}
			stage ('BUILD') {
				steps {
					sh 'mvn clean install'
				}
				post{
					success{
						echo "Archiving the Artifacts"
						archiveArtifacts artifacts: '**/target/*.war' 
					}
				}
			)
			stage ('Deploy to Tomcat server) {
				steps {
					deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.93.152.247:8080/')], contextPath: null, war: '**/*.war'
				}
			}
		}	
	}
