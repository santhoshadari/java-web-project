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
	        stage('Sonarqube') {
			    environment {
                         scannerHome = tool 'sonarqubescanner'
                        }
		        steps {
				    bat label: '', script: '${scannerHome}/bin/sonar-scanner'
				} 
		   }		
		}
 }