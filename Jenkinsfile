pipeline {
    agent {
        node {
            label 'jenkins-flutter-agent'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/flutter-project.git'
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
