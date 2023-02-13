#!/usr/bin/env groovy
pipeline{

      agent {
                docker {
                image 'maven:3-openjdk-11'
                args '-v $HOME/.m2:/root/.m2'
                }
            }
        
        stages{
		stage('Quality Gate Statuc Check'){
                  steps{
                      script{
                      withSonarQubeEnv('sonarserver') { 
                      sh "mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=admin"
		    sh "mvn clean install"
                  }
                }  
              }
	}
	}
