pipeline {
    agent {
        docker {
            image 'my-local-image:local' // Specify the name and tag of your local image
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
}
