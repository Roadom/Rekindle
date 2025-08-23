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
            archiveArtifacts artifacts: 'rekindle/build/app/outputs/flutter-apk/app-*.apk', fingerprint: true
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}
