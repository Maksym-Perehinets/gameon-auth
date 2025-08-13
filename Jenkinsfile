pipeline {
  agent any
  tools {
    jdk 'JDK8'
  }
  environment {
    DOCKER_REGISTRY = 'testgyuhijhg-fafxfabsfjaseqev.azurecr.io'
    ACR_SP_CLIENT_ID = '9f756af3-eed2-4acc-aebe-bfac41cc80fd'
  }
  stages {
    stage('Azure login') {
      steps {
        sh 'az login --identity --client-id ${ACR_SP_CLIENT_ID}'
        sh 'az acr login --name ${DOCKER_REGISTRY}'
      }
    }
    stage('Build') {
      steps {
        sh './gradlew build'
        sh 'docker build -t ${DOCKER_REGISTRY}/gameon-auth auth-wlpcfg'
      }
    }
    stage('Publish Docker Image') {
      steps {
        sh 'docker push ${DOCKER_REGISTRY}/gameon-auth'
      }
    }
  }
}