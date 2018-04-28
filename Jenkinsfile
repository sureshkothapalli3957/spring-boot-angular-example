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
  }
}