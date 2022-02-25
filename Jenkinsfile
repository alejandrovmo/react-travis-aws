pipeline{
    agent {
        docker {
            image 'docker'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages{        
        stage('Git clone'){
            steps{
                git 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('Build stage'){
            steps{
                sh 'docker build -t devimage -f Dockerfile.dev .'
            }
        }
    }
}