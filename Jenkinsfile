pipeline {
  agent any
  tools {
    jdk 'JDK8'
  }
  stages {
    stage('Build') {
      steps {
        sh './gradlew build'
        sh 'docker build -t gameon-auth -f auth-wlpcfg/Dockerfile .'
      }
    }
  }
}