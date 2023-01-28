pipeline {
	agent any
	tools {
	    maven 'maven3'
	}
	stages {
	    stage('Build') {
	        steps {
	           sh script: 'mvn clean package'
	        }
	    }
	    stage('Upload War to Nexus') {
	        steps {
	        	   nexusArtifactUploader artifacts: [
            	       [
            	          artifactId: 'simple-app-jenkins',
            	          classifier: '',
            	          file: 'target/simple-app-jenkins-0.0.1.war',
            	          type: 'war'
            	       ]
            	   ],
            	   credentialsId: 'nexus3',
                   groupId: 'in.javahome',
                   nexusUrl: 'localhost:8081',
                   nexusVersion: 'nexus3',
                   protocol: 'http',
                   repository: 'simple-app-jenkins-release',
                   version: '0.0.1
	        }
	    }
	}
}
