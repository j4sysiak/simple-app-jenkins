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
            	          artifactId: 'simple-app',
            	          classifier: '',
            	          file: 'target/simple-app-0.0.9.war',
            	          type: 'war'
            	       ]
            	   ],
            	   credentialsId: 'nexus3',
                   groupId: 'in.javahome',
                   nexusUrl: 'localhost:8081',
                   nexusVersion: 'nexus3',
                   protocol: 'http',
                   repository: 'simpleapp-release',
                   version: '0.0.9
	        }
	    }
	}
}
