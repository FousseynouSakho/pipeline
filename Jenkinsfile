pipeline {
  agent any
  stages {
    stage('recuperation des sources') {
      steps {
        git(branch: 'master', credentialsId: 'loginhub', url: 'https://github.com/FousseynouSakho/pipeline')
      }
    }
    stage('build') {
      steps {
        sleep(unit: 'MINUTES', time: 10)
        timestamps()
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