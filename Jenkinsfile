pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello Muta'
                nodejs('bootcampnodejs 12 16 1') {
                    sh 'npm install'
                }
                echo 'Goodbye fatta'
            }
        }
    }
}