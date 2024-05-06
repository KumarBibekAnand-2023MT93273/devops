pipeline {
    agent any
     tools {
        // Install the Maven version configured as "M3" and add it to the path.
        jdk "JDK17"
        maven "Maven-3.9.6"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/KumarBibekAnand-2023MT93273/devops.git'
            }
        }
        stage('Build and Compile') {
            steps {
                bat 'mvn clean compile'
            }
        }
    }
    
    post {
        always {
            // Clean up workspace
            cleanWs()
        }
         // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
        success {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
         }
        failure {
            echo 'Build and compile failed!'
            // Optionally, you can send notifications or take other actions on failure
        }
    }
}
