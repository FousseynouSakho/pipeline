pipeline {
  agent any
	  stages {
		stage('recuperation des sources') {
		  steps {
			git(branch: 'master', credentialsId: 'loginhub', url: 'https://github.com/FousseynouSakho/pipeline.git')
		  }
		}
		stage('build maven') {
		  steps {
			bat(script: 'runmaven.bat', encoding: 'utf-8')
		  }
		}
		stage('publication') {
			steps { 
			nexusArtifactUploader artifacts: [ [artifactId: 'jpetstore', type: 'war', classifier: 'debug', file: 'target/jpetstore.war']
				],
			 nexusVersion: 'nexus3',
			 protocol: 'http', 
			 nexusUrl: 'localhost:8081/', 
			 groupId: 'jpetstore',
			 version: '1.0-SNAPSHOT', 
			 repository: 'maven-snapshots', 
			 credentialsId: '807b6526-906b-4bc7-937f-bd6fae027d1c' }
		}
	  }
  }
