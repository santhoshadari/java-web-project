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
		    stage('Maven deploy') {
		        steps {
				    bat label: '', script: 'mvn deploy'
				} 
		   }
		}
    }		
/*            stage('Package publish nexus') {
			     environment {
				    def pom = readMavenPom file: 'pom.xml'
				 }
			    steps {        
                    nexusArtifactUploader artifacts: [
                                 [artifactId: 'java-web-project', classifier: 'debug', file: 'java-web-project-1.0-SNAPSHOT.war', type: 'war'], 
                                 //[artifactId: 'nexus-artifact-uploader', classifier: 'debug', file: 'nexus-artifact-uploader.hpi', type: 'hpi']
                                  ], 
                    credentialsId: 'ed28e1dd-8837-47bb-9acf-d5dffdd5d90f', 
                    groupId: 'com.sampleweb.web', 
                    nexusUrl: 'localhost:8081/nexus', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'java-web-project', 
                    version: '1.0-SNAPSHOT'
					 nexusPublisher nexusInstanceId: 'sonarnexuslocal3', \
                           nexusRepositoryId: 'java-web-project', \
                           packages: [[$class: 'MavenPackage', \
                           mavenAssetList: [[classifier: '', extension: '', filePath: "target\\${pom.artifactId}-${pom.version}.${pom.packaging}"], \
                                                    [classifier: 'sources', extension: '', filePath: "target\\${pom.artifactId}-${pom.version}-sources.${pom.packaging}"]], \
                            mavenCoordinate: [artifactId: "${pom.artifactId}", \
                            groupId: "${pom.groupId}", \
                            packaging: "${pom.packaging}", \
                            version: "${pom.version}-${env.BUILD_NUMBER}"]]]
				}			
            }   
		}
    }*/	
/*	        stage('Sonarqube analysis') {
			    environment {
                         scannerHome = tool 'sonarqubescanner'
						 //withSonarQubeEnv(credentialsId: '1c3e7544-b78d-49db-abd4-c3176710fb90', installationName: 'sonarqubescanner') { // You can override the credential to be used
                        }
		        steps {
				         //bat label: '', script: 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
				         //def scannerHome = tool 'sonarqubescanner';
						//withSonarQubeEnv ('sonarqube') {
					     //bat "${scannerHome}/bin/sonar-scanner"
						 //bat "\"${scannerHome}\\StartSonar.bat\"" -D sonar.login=admin -D sonar.password=admin
                         bat label: '', script: 'mvn sonar:sonar'
						//}				
		       // }   
		   //}		
		     stage('Quality Gate') {
                steps {
                      timeout(time: 1, unit: 'HOURS') {
                          def gg = waitForQualityGate()
					      if (gg.status != 'ok') {
						    //error "pipeline aborted due to quality gate failure: $(gg.status)"
						  }
                    }
                }
            }
		}
    }
*/