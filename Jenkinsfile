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
    stage('qualimetrie') {
      steps {
		withSonarCubeEnv('sonar'){
        bat(script: 'runsonar.bat', encoding: 'utf-8')

		}
      }
    }
	stage('qualityGate') {
      steps {
	  sleep 10
		timeout(time: 10, unit: 'MINUTES'){
       waitForQualityGate (abortPipeline: true)

			}
		}
	}
    stage('publication') {
      steps {
        nexusArtifactUploader(artifacts: [ [artifactId: 'jpetstore', type: 'war', classifier: 'debug', file: 'target/jpetstore.war']
                				], nexusVersion: 'nexus3', protocol: 'http', nexusUrl: 'localhost:8081/', groupId: 'jpetstore', version: '1.0-SNAPSHOT', repository: 'maven-snapshots', credentialsId: '501dc971-0827-4619-9971-de58945bbc9b')
      }
    }
  }
}