pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Roadom/Rekindle.git'
            }
        }

        stage('Build') {
            steps {
                sh 'flutter build apk --debug'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'flutter test'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/app/outputs/flutter-apk/app-*.apk', fingerprint: true
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}
