pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'build'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'test'
          }
        }

        stage('test fonctionnel') {
          steps {
            echo 'test fonctionnel '
          }
        }

        stage('smoke test ') {
          steps {
            echo 'smoke test '
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'deploy'
      }
    }

  }
}