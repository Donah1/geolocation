pipeline {
    agent any
    tools{
        maven 'M2_HOME'
    }
    environment {
        registry = '259759258639.dkr.ecr.ap-south-1.amazonaws.com/geolocation_ecr_rep'
        dockerimage = '' 
    }    
    stages {
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Donah1/geolocation.git'
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
        // Building Docker images
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        // Uploading Docker images into AWS ECR
        stage('Pushing to ECR') {
            steps{
                script {
                    sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 259759258639.dkr.ecr.ap-south-1.amazonaws.com'
                    sh 'docker push 259759258639.dkr.ecr.ap-south-1.amazonaws.com/geolocation_ecr_rep:latest'
                }
            }
        }
    }
}