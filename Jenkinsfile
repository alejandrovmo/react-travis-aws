pipeline { 
    environment {
        registry = "varmon/jenkinsslve"
        registryCredential = 'dockerhub'
    }
    agent {Docker} {label 'testslave'}
    stages {
        stage('Git clone') {
            steps {
                git branch: "development", url: 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('Build stage'){
            steps{
                sh 'docker build -t devimage -f Dockerfile.dev .'
            }
        }    
    }
}