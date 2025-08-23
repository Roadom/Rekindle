pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'docker run --rm node:16-alpine node --version'
            }
        }
    }
}
