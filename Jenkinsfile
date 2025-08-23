pipeline {
    agent {
        docker {
            image 'ghcr.io/cirruslabs/flutter:3.36.0-0.1.pre'
            args '-u 1000:1000'
            reuseNode true
        }
    }
    stages {
        stage('Build') {
            steps {
                dir('rekindle') {  
                    sh '''
                        git config --global --add safe.directory /sdks/flutter
                        flutter build web
                    '''
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
                    sh 'echo "Simulated deployment complete"'
                }
            }
        }
        stage('Integration Test') {
            steps {
                dir('rekindle') {
                    sh 'echo "Running dummy integration test"'
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
