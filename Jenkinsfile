pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                echo 'Hello bob'
                nodejs('bootcampnodejs 12 16 1') {
                    sh 'npm install'
                }
                echo 'Goodbye bob'
            }
        }
        stage('testing') {
            steps {
                echo 'Hello terry'
                nodejs('bootcampnodejs 12 16 1') {
                    sh 'npm test'
                }
                echo 'Goodbye terry'
            }
        }
        stage('scanning') {
            steps {
                echo 'Hello Suzy'
                echo 'sonar-cube  something someting '
                echo 'Goodbye Suzy'
            }
        }
    }
}