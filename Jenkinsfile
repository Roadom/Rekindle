pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
        }
    }
    environment {
    GRADLE_OPTS = "-Dorg.gradle.daemon=false"
    }
    stages {
        stage('Build') {
            steps {
                dir('rekindle') {  
                    sh 'flutter build apk --debug'
                }
            }
        }
        stage('Unit Test') {
            steps {
                dir('rekindle') { 
                    sh 'flutter test'
                }
            }
        }
    }
}
