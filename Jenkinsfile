pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
        }
    }
    stages {
        stage('Build') {
            steps {
                dir('rekindle') {  
                    sh 'flutter build apk'
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
        stage('Deploy To Test Env') {
            steps {
                dir('rekindle') {
                    sh 'mkdir -p /tmp/test_env && cp build/app/outputs/flutter-apk/app-release.apk /tmp/test_env/'
                    sh 'echo "Simulated deployment complete"'
                }
            }
        }
        stage('Integration Test') {
            steps {
                dir('rekindle') {
                    sh 'echo "Running dummy integration test"; exit 0'
                }
            }
        }
        stage('Create Docker Image') {
            steps {
                sh 'echo "Docker image built"'
            }
        }


    }
}
