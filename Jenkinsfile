pipeline{
    agent any
    stages{
        stage('build'){
            steps{
                docker build -t devimage -f Dockerfile.dev .
            }
        }
    }
}