pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
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
