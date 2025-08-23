pipeline {
    agent any

    stages {
        stage('TEST') {
            steps {
                dir('rekindle'){
                    sh 'flutter test'
                }
            }
        }
        stage('BUILD') {
            steps {
                dir('rekindle'){
                    sh '''
                    #!/bin/sh
                    flutter build apk
                    '''
                }
            }
        }
    }
}