pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
      args '-p 3000:3000'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deploy') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        // input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
        sh 'read -t 60 -p "React App akan berjalan selama 1 menit"'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}