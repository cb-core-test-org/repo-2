pipeline {
  agent {
    kubernetes {
      label 'k8s-examples'
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: golang
    image: golang:1.11.0-alpine
    command: ['cat']
    tty: true
  - name: curl
    image: appropriate/curl:latest
    command: ['cat']
    tty: true
"""
    }
  }
  stages {
    stage('Handle master') {
      when {
        branch 'master'
      }
      steps {
        container('golang') {
          sh 'env | sort'
          sh 'go version'
        }
      }
    }
  }
}
