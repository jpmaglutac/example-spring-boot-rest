pipeline {

    agent any
    
    stages {
        stage("Test") {
            steps {
                withMaven(maven: 'mvn-default')
                bat 'mvn clean test'
                junit 'target'
            }
        }
        
        stage("Build") {
            steps {
                bat 'mvn package'
            }
        }
        
        stage("Deploy") {
            steps {
                echo "deploy"
            }
        }
              
    }

}
