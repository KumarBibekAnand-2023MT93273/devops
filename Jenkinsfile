pipeline {
    agent any
    tools {
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
                bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Run Tests') {
            steps {
                bat "mvn test"
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
        success {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
        failure {
            echo 'Build and compile failed!'
        }
    }
}
