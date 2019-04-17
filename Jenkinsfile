pipeline {
  agent {
    docker {
      image 'gradle:4.8.1'
      label 'centos'
    }
  }
  stages {
    stage('Show Versions') {
      // when { tag "*" }
      steps {
        sh '''
          java -version
          gradle -v
        '''.trim()
      }
    }
    stage('Build and Test') {
      // when { tag "*" }
      parallel {
        stage('Build') {
          steps {
            sh 'gradle -p complete assemble'
          }
        }
        stage('Test') {
          steps {
            sh 'gradle -p test'
          }
        }
      }
    }
  }
}
