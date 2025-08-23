pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent (ghcr.io/cirruslabs/flutter:3.36.0-0.1.pre)'
        }
    }
    stages {
        stage('Dependencies') {
            steps {
                dir('rekindle') {
                    sh 'flutter pub get'
                }
            }
        }
        stage('Build') {
            steps {
                dir('rekindle') {  
                    sh 'flutter build apk --debug --verbose'
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

    post {
        success {
            archiveArtifacts artifacts: 'my_app/build/app/outputs/flutter-apk/app-*.apk', fingerprint: true
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}
