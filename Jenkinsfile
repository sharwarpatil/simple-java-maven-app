pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    tools {
        maven 'Maven3'   // This name must match what you configured
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
   stage('Deliver') { 
    steps {
        script {
            // First check what's in the .sh file
            bat 'type jenkins\\scripts\\deliver.sh'
            
            // Then create or call the appropriate script
            bat 'jenkins\\scripts\\deliver.bat'  // after you create it
        }
    }
}
    }
     
}








