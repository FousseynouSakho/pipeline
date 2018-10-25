pipeline {
  agent any
  stages {
    stage('recuperation des sources') {
      steps {
        git(branch: 'master', credentialsId: 'loginhub', url: 'https://github.com/FousseynouSakho/pipeline')
      }
    }
    stage('build maven') {
      steps {
        sleep(unit: 'MINUTES', time: 10)
        bat(script: 'runmaven.bat', encoding: 'utf-8')
      }
    }
    stage('results') {
      steps {
        echo 'message'
        sleep 10
      }
    }
  }
}