pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=sedecgroup -Dsonar.organization=sedecgroup -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=d236b165ca2c0305acc4051d915d9e7f5f7b9766'
			}
	     }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
                       } 
     } 
  }
}
