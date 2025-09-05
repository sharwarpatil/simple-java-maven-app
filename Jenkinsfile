pipeline {
    agent any

    tools {
        maven 'Maven3'   // This name must match what you configured
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
    }
}
