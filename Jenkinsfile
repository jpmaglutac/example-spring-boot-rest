pipeline {

    agent any
    
    stages {
        stage("Test") {
            steps {
                withMaven(maven: 'mvn-default') {
                    bat 'mvn clean test'
                    junit 'target/surefire-reports/*'
                }
            }
        }
        
        stage("Build") {
            steps {
                withMaven(maven: 'mvn-default') {
                    bat 'mvn package'
                }
            }
        }
        
        stage("Deploy") {
            steps {
                echo "deploy"
            }
        }
              
    }

}
