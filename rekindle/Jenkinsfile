pipeline {
    agent {
        docker {
            image 'cirrusci/flutter:latest'   // Flutter SDK preinstalled
            args '-u root:root'              // optional: run as root
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'flutter pub get'
                sh 'flutter build apk --debug'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'flutter test'
            }
        }

        stage('Deploy To Test Env') {
            steps {
                echo 'Deploying APK to test environment...'
                // add adb / Firebase App Distribution / TestFlight step here
            }
        }

        stage('Integration Test') {
            steps {
                echo 'Running integration tests...'
                // e.g. flutter drive or integration_test package
            }
        }

        stage('Create Docker Image') {
            steps {
                sh 'docker build -t my-flutter-app .'
            }
        }
    }
}
