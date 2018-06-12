pipeline {

    agent any
    
    stages {
        stage("Test") {
            steps {
                withMaven(maven: 'mvn-default') {
                    bat 'mvn clean test'
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage("Build") {
            steps {
                withMaven(maven: 'mvn-default') {
                    bat 'mvn package'
                    archiveArtifacts 'target/example-spring-boot-rest-1.0-SNAPSHOT.jar'
                }
            }
        }
        
        stage("Deploy") {
            steps {
                bat 'java -jar target/example-spring-boot-rest-1.0-SNAPSHOT.jar'
            }
        }
              
    }

}
