pipeline {
     triggers {
  pollSCM('* * * * *')
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
                echo 'test'
                sleep 5
            }
        }
          stage('deploy') {
            steps {
                echo 'deploy'
                sleep 4
            }
        }
    }
}