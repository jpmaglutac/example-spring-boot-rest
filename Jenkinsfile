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
                bat 'javaw -jar target/example-spring-boot-rest-1.0-SNAPSHOT.jar'
            }
        }
        
        stage("API Test") {
            steps {
                dir("tests") {
                    bat 'newman run example-spring-boot-rest.postman_collection.json -r "cli,html"'
                    publishHTML 'newman/*.html'
                }
            }
        }
              
    }

}
