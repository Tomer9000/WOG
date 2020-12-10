pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: wog1
spec:
  containers:
  - name: wog1
    image: tomer9000/wog:v2
"""
    }
  }
  stages {
    stage('run e2e') {
      steps {
        container('wog1') {
          sh 'python /root/test_wog/test_e2e.py --driver /root/chromedriver'
        }
      }
    }
  }
}