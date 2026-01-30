pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') {
            steps {
                // Using your absolute path
                sh '/home/cloud/gradle-8.5/bin/gradle clean test'
            }
        }
       stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '/home/cloud/gradle-8.5/bin/gradle sonarqube'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                sh '/home/cloud/gradle-8.5/bin/gradle jar'
                archiveArtifacts artifacts: 'build/libs/*.jar', allowEmptyArchive: false
            }
        }
    }
}
