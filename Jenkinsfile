pipeline{
    agent { docker {image 'docker'}}
    stages{        
        stage('Git clone'){
            steps{
                git 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('Build stage'){
            steps{
                sh 'docker build -t devimage -f Dockerfile.dev . --privileged --name jenkins jenkins'
            }
        }
    }
}