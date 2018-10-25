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
  }
}