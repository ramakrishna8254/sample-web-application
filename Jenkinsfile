#!/usr/bin/env groovy
pipeline{

      agent {
                docker {
                image 'maven:3-openjdk-11'
                args '-v $HOME/.m2:/root/.m2'
                }
            }
        
        stages{
		stage('Quality Gate Status Check'){
                  steps{
                      script{
                      withSonarQubeEnv('sonarserver') {
			      withCredentials([usernameColonPassword(credentialsId: 'SONARLOGIN', variable: 'sonarlogin')]) {
    				sh "mvn sonar:sonar -Dsonar.login=$sonarlogin -Dsonar.password=$sonarlogin"
}
                      
		    sh "mvn clean install"
                  }
                }  
              }
	}
	}
}
