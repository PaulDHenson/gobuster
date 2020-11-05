pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh 'go build'
      }
    }

    stage('Test') {
      steps {
        sh 'go test ./...'
      }
    }

    stage ('Remove Dist') {
	steps {
	    sh 'rm -r ./dist'
	}
    }

    stage ('Release') {

      environment {
        GITHUB_TOKEN = credentials('github-token')
      }

      steps {
        sh 'curl -sL https://git.io/goreleaser | sh'
      }
    }
  }
}
