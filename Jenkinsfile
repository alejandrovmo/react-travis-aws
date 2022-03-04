pipeline {
  Docker {label 'testslave'}
  stages {
    stage('Git clone') {
        steps {
            git branch: "development", url: 'https://github.com/alejandrovmo/react-travis-aws.git'
      }
    }
    stage('Build stage'){
        steps{
            docker ps
        }
    }    
  }
}