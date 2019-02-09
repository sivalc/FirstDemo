pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {
        stage ('Build') {
            docker { 
                image maven
            }
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

        stage('Code Quality') {
            steps {
             sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.1.8:9000 -Dsonar.login=fa023b77f86a095a2a7206f3e6d3b3ca2544715e'

            }
        }    

    }

    post {
        always {
          echo "echo Done"
          deleteDir()
        }
        changed {
          echo "echo something changes"
        }
        failure {
          echo "echo FAILED"
        }
        success {
          echo "echo Successful"
        }
        unstable {
          echo "echo Unstable"
        }
    }
}    
