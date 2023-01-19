pipeline {
     agent any
     tools {
        maven 'M2_HOME'
     }
    stages {
        stage('maven package') {
        steps {
             sh 'mvn clean'
             sh 'mvn install'
             sh 'mvn package'
        }
    }
          stage('Test') {
        steps {
            sh 'mvn clean'
        }
    }
        stage('test') {
        steps {
            sh 'test'
         
        }
    }
        stage('deploy') {
        steps {
            echo 'deploy'
           
         }
                }
            }
        }    
         