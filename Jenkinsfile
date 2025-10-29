pipeline {
  agent any
  tools {
    nodejs 'NodeJS'
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Archive Artifact') {
      steps {
        sh 'mkdir -p dist && echo "artifact built successfully" > dist/artifact.txt'
        archiveArtifacts artifacts: 'dist/**', fingerprint: true
      }
    }
  }
  post {
    success {
      echo '🎉 Pipeline completed successfully!'
    }
    failure {
      echo '❌ Pipeline failed!'
    }
  }
}
