pipeline {
  agent any
  tools {
    jdk 'JDK8'
  }
  stages {
    stage('Build') {
      steps {
        sh './gradlew build'
      }
    }
  }
}