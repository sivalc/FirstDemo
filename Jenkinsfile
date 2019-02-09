pipeline {
    agent any

    stages {
        

        stage ('Build') {
            steps {
                sh 'mvn clean -DskipTests install' 
            }
    
            post
                success {
                    //junit 'target/surefire-reports/**/*.xml' 
                    archiveArtifacts artifacts: '**/target/*.jar
                }
            }
        }
    }
