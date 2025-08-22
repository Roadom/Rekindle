pipeline {
    agent {
        docker {
            image 'ghcr.io/cirruslabs/flutter:3.36.0-0.1.pre'
            args '-u root:root'   // so it runs as root, avoids permissions issues
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Build'
            }
        }

        stage('Unit Test') {
            steps {
                echo 'unit test'
            }
        }

        stage('Deploy To Test Env') {
            steps {
                echo 'Deploying APK to test environment...'
            }
        }

        stage('Integration Test') {
            steps {
                echo 'Running integration tests...'
            }
        }

        stage('Create Docker Image') {
            steps {
                echo 'Creating docker image...'
            }
        }
    }
}
