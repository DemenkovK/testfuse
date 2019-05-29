pipeline {
    agent any
    
    tools {
        maven "maven3"
    }
    
    stages{
        stage ('checkout') {
             steps {
            
 	        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'c5a9c5f5-6735-4c8c-83cc-28232414c544', url: 'https://github.com/DemenkovK/testfuse']]]) 
             }
        }
        stage ('maven build') {
            steps {
        	withMaven(maven: 'maven3') { 
 		        	sh "mvn package " 
		        	} 
		                  	}
         }
         stage ('moving to tomcat') {
            steps {
              //  sh 'scp target/*.war root@192.168.0.7:/var/lib/tomcat8/webapps/'
              sh label: '', script: 'scp target/*.war root@192.168.0.7:/var/lib/tomcat8/webapps/'
        }
            }
        }}
