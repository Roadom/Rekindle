pipeline {
    agent {
          docker {
            image 'ghcr.io/cirruslabs/flutter:3.36.0-0.1.pre'
            args '-u root:root -v /var/jenkins_home/.pub-cache:/root/.pub-cache -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Build') {
            steps {
                dir('rekindle') {  
                    sh 'flutter build web'
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
