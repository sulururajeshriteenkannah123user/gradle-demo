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
