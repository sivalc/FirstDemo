pipeline {
    agent any

    stages {
        

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            
       stage('Download') {
            steps {
                sh 'mkdir war'
                sh 'echo "not a artifact file" > war/build.js'
                sh 'echo "artifact file" > js/build.war'
                
              }
        }
    }
    post {
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                    
                    archiveArtifacts artifacts: '**/*.min.*', onlyIfSuccessful: true
                }
            }
        }
    }
}
