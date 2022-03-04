pipeline {
  agent {label 'testslave'}
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'development', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('Git clone') {
        steps {
            git branch: "${params.BRANCH}", url: 'https://github.com/alejandrovmo/react-travis-aws.git'
      }
    }
    stage('Build stage'){
        steps{
            sh 'docker build -t devimage -f Dockerfile.dev .'
        }
    }    
  }
}