pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'build'
        echo 'la construction a commencé'
        bat 'mvn -DskipTests clean package'
        echo 'La construction est terminé '
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'smoke'
            bat 'mvn -Dtest="com.exemple.testingweb.smoke.**" test'
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('test fonctionnel') {
          steps {
            echo 'test fonctionnel '
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
          }
        }

        stage('smoke test ') {
          steps {
            echo 'smoke test '
            bat 'mvn -Dtest="com.example.testingweb.functional.**" test'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'deploy'
        bat 'mvn -DskipTests install'
      }
    }

  }
}