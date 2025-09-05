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
            echo "Current directory: ${pwd()}"
            bat 'dir jenkins\\scripts'  // Verify script exists
            bat 'type jenkins\\scripts\\deliver.bat'  // Show script contents
            
            // Run with error capture
            def result = bat(script: 'jenkins\\scripts\\deliver.bat', returnStatus: true)
            if (result != 0) {
                error("Delivery script failed with exit code: ${result}")
            }
        }
    }
}
    }
     
}







