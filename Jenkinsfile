pipeline {
    agent {
        docker {
            image 'ghcr.io/cirruslabs/flutter:3.36.0-0.1.pre'
            args '-u root:root -v $HOME/.gradle:/root/.gradle -v $HOME/.pub-cache:/root/.pub-cache'
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
