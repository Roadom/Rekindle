pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
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

    post {
        success {
            archiveArtifacts artifacts: 'my_app/build/app/outputs/flutter-apk/app-*.apk', fingerprint: true
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}
