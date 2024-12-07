pipeline {
    agent any  // All stages will run on any available agent
    tools {
        maven 'maven3'  // Refer to the Maven version you've configured
    }
    
    stages {

        // Checkout code from GitHub repository
        stage('Checkout code') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/max-az-10/maven_sonarqube.git'
            }
        }

        // Build the project
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        // Run SonarQube analysis
        stage('Sonarqube') {
            steps {
                withSonarQubeEnv('SonarQube-Server') {  // Ensure 'SonarQube_server' is defined in Jenkins configuration
                    sh 'mvn sonar:sonar'
                }
            }
        }

        // Simple stage to verify echo
        stage('Verify echo!!') {
            steps {
                sh 'echo "This pipeline works as expected!!!"'
            }
        }
    }
}
