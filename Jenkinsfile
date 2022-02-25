pipeline{
    agent any
    stages{        
        stage('Git clone'){
            steps{
                git 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('Build stage'){
            steps{
                sh 'docker build -d --network=host -t devimage -f Dockerfile.dev .'
            }
        }
    }
}