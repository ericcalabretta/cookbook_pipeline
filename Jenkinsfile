pipeline {
  agent any
  stages {
    stage('Pre-reqs') {
      steps {
        sh '''
          # Make sure ChefDK is installed
          if [ ! $(which chef)]
          then
            echo "Installing ChefDK"
            wget https://packages.chef.io/files/stable/chefdk/2.4.17/ubuntu/16.04/chefdk_2.4.17-1_amd64.deb
            sudo dpkg -i chefdk_2.4.17-1_amd64.deb
          else
            echo "ChefDK is installed"
          fi  
          '''
      }
    }

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
