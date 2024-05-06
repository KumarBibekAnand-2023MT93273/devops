pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/KumarBibekAnand-2023MT93273/devops.git'
            }
        }
        stage('Build and Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
    }
    
    post {
        always {
            // Clean up workspace
            cleanWs()
        }
        success {
            echo 'Build and compile successful!'
        }
        failure {
            echo 'Build and compile failed!'
            // Optionally, you can send notifications or take other actions on failure
        }
    }
}
