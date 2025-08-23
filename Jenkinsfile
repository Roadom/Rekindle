pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
            pull false
        }
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
