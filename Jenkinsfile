pipeline {
       agent any
	   environment {
	       name = "santhosh"
	    }
		//tools {
		   //  jdk "java 1.8"
		    //maven "Maven-3.5.3"
		//}
		parameters{
		        booleanParam(defaultValue: false, description: 'Simulate the promotion', name: 'SIMUL')
		}
		stages {
		    stage('SCM-checkout') {
			   steps {
			       git 'https://github.com/santhoshadari/java-web-project.git'
			   }
			}
		    stage('Maven install') {
		        steps {
				    bat label: '', script: 'mvn clean install'
				} 
		   }	
			stage('Maven sonarscan') {
		        steps {
				    bat label: '', script: 'mvn sonar:sonar'
				} 
		   }	
			stage('Maven compile') {
		        steps {
				    bat label: '', script: 'mvn clean validate compile'
				} 
		   }	
			stage('Maven package') {
		        steps {
				    bat label: '', script: 'mvn package'
				} 
		   }	
	        /*stage('Sonarqube analysis') {
			    /*environment {
                         scannerHome = tool 'sonarqubescanner'
						 //withSonarQubeEnv(credentialsId: '1c3e7544-b78d-49db-abd4-c3176710fb90', installationName: 'sonarqubescanner') { // You can override the credential to be used
                        }*/
		        steps {
				         //bat label: '', script: 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
				         //def scannerHome = tool 'sonarqubescanner';
						//withSonarQubeEnv ('sonarqube') {
					     //bat "${scannerHome}/bin/sonar-scanner"
						 //bat "\"${scannerHome}\\StartSonar.bat\"" -D sonar.login=admin -D sonar.password=admin@123
                         bat label: '', script: 'mvn sonar:sonar'
						//}				
		        }   
		   }		
		     stage('Quality Gate') {
                steps {
                      timeout(time: 1, unit: 'HOURS') {
                          def gg = waitForQualityGate()
					      if (gg.status != 'ok') {
						    //error "pipeline aborted due to quality gate failure: $(gg.status)"
						  }
                    }
                }
            }*/
		}
    }