pipeline {
    agent any  // All stages will run on any available agent

    stages {

        // Checkout code from GitHub repository
        stage('Checkout code') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/max-az-10/maven_sonarqube.git'
            }
        }

        // Simple stage to verify echo
        stage('Verify echo!!') {
            steps {
                sh 'echo "This is to verify echo!"'
            }
        }

        // Build and run SonarQube analysis
        stage('build & sonarqube') {
            steps {
                withSonarQubeEnv('SonarQube_server') {  // Ensure 'SonarQube_server' is defined in Jenkins configuration
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
