pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        echo 'hello world'
        sh 'npm install'
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'pwd'
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('ACK') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
      }
    }

    stage('Deploy') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}