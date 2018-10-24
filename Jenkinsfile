pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        timestamps()
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