pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm [cite: 251]
            }
        }
        stage('Build & Test') {
            steps {
                // Using your absolute path
                sh '/home/cloud/gradle-8.5/bin/gradle clean test' [cite: 252]
            }
        }
        stage('Archive Artifact') {
            steps {
                sh '/home/cloud/gradle-8.5/bin/gradle jar' [cite: 254]
                archiveArtifacts artifacts: 'build/libs/*.jar', allowEmptyArchive: false [cite: 255]
            }
        }
    }
}
