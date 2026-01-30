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
                sh 'chmod +x gradlew' // If using wrapper, otherwise just 'gradle'
                sh 'gradle clean test' 
            }
        }
        stage('Archive Artifact') {
            steps {
                sh 'gradle jar'
                archiveArtifacts artifacts: 'build/libs/*.jar', allowEmptyArchive: false
            }
        }
    }
}
