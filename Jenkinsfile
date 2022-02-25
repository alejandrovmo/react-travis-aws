pipeline{
    agent any
    stages{        
        stage('Git clone'){
            steps{
                git 'https://github.com/alejandrovmo/react-travis-aws.git'
            }
        }
        stage('build'){
            steps{
                docker build -t devimage -f Dockerfile.dev .
            }
        }
    }
}