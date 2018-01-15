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
        stage('Syntax') {
          steps {
            sh 'chef exec cookstyle . --format progress'
          }
        }
        stage('Unit') {
          steps {
            sh 'chef exec rspec --format progress --format RspecJunitFormatter --out rspec_junit.xml'
          }
        }
      }
    }
  }
}
