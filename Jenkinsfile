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
                    sh '/home/cloud/gradle-8.5/bin/gradle sonar -Dsonar.token=squ_d6184eb31bcb718fba20d34554a5a70649c4f7af'
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
