pipeline{
    agent none
    stages{        
        stage('Git clone'){
            steps{
                git 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('Build stage')
            agent { docker {image 'docker'}}
        {
            steps{
                sh 'docker build -t devimage -f Dockerfile.dev .'
            }
        }
    }
}