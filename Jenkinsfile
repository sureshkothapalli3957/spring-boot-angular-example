pipeline {
  agent any
  triggers { pollSCM('* * * * *') }
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
        bat(script: 'packer build packer.json', returnStatus: true, returnStdout: true)
      }
    }
  }
}