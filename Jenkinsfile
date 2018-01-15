pipeline {
  agent any
  stages {


    stage('Verify') {
      parallel {
        stage('Lint') {
          steps {
            sh 'chef exec foodcritic .'
          }
        }
      }
    }
  }
}
