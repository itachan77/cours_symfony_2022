pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'stage : Build'
        bat 'composer install'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'php bin/phpunit tests/unitaire'
          }
        }

        stage('integration') {
          steps {
            sh 'php bin/phpunit tests/integration'
          }
        }

        stage('fonctionnel') {
          steps {
            sh 'php bin/phpunit tests/fonctionnel'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        sh 'symfony server:start'
      }
    }

  }
}