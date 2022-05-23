pipeline {
    agent any
    tools{
        maven 'M2_HOME'
    }
    environment {
    registry = '076892551558.dkr.ecr.us-east-1.amazonaws.com/devop_repository'
    registryCredential = 'jenkins-ecr'
    dockerimage = ''
  }
    stages {
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Hermann90/helloworld_jan_22.git'
            }
        }
        stage('Code Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Build Image') {
            steps {
                script{
                    dockerImage =  Shell Script -- docker build -t "$JD_IMAGE"
                } 
            }
        }
        stage('Deploy image') {
            steps{
                script{ 
                    docker.withRegistry("https://"+812308457545.dkr.ecr.us-east-1.amazonaws.com/devops_repository) {
                        dockerImage.push()
                    }
                }
            }
        }  
    }
}
