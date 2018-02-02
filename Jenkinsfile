pipeline {
  agent any

  environment {
    TAG = "liatrio/w3af:latest"
  }

  stages {
    stage("Build") {
      steps {
        sh """
           cp extras/docker/Dockerfile . && \
           cp extras/docker/.dockerignore . && \
           docker build -t ${TAG} .
           """
      }
    }

    stage("Push") {
      steps {
        sh "docker push ${TAG}"
      }
    }

    stage("Cleanup") {
      steps {
        sh """
           rm -rf Dockerfile && \
           rm -rf .dockerignore
           """
      }
    }
  }
}
