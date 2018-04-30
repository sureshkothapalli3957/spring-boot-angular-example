pipeline {
  agent any
  stages {
    stage('Build Backend') {
      steps {
        bat(script: 'cd server && mvnw package', returnStatus: true, returnStdout: true)
      }
    }
    stage('Archive ') {
      steps {
        archiveArtifacts 'server/target/*.jar'
      }
    }
    stage('Build Ami') {
      steps {
        bat(script: 'packer build packer.json > output.txt', returnStatus: true, returnStdout: true)
      }
    }
  }
  environment {
    AWS_SHARED_CREDENTIALS_FILE = 'C:\\Users\\Welcome\\.aws\\credentials'
  }
  triggers {
    pollSCM('* * * * *')
  }
}