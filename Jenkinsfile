pipeline {
    agent any

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean -DskipTests install' 
            }
    
            post {
                success {
                    //junit 'target/surefire-reports/**/*.xml' 
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Code Quality')
            steps {
             sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.1.8:9000 -Dsonar.login=fa023b77f86a095a2a7206f3e6d3b3ca2544715e'

            }
        }    

    }
}    
