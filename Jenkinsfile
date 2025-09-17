pipeline {
  agent any
  options { timestamps() }
  stages {
    stage('Checkout') {
      steps {
        // If using "Pipeline script from SCM", this pulls your repo
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh '''
          set -e
          mkdir -p build
          javac -d build src/Hello.java
        '''
      }
    }
    stage('Test') {
      steps {
        sh '''
          set -e
          OUT=$(java -cp build Hello)
          echo "Output: $OUT"
          test "$OUT" = "Hello, Jenkins!"
        '''
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'build/**', fingerprint: true
    }
  }
}
