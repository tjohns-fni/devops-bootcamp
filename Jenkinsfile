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
        stage('docker') {
            steps {
                echo 'Hello dolly'
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')])  {
                sh '''
                wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
dpkg -i ./docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
apt-get update
apt-get install -y awscli
docker build -t workshopuser6:latest .
docker tag workshopuser6:latest workshopuser4:${BUILD_NUMBER}
docker tag workshopuser6:latest 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser6:latest
$(aws ecr get-login --region us-east-1 | sed 's/-e none//g')
docker push 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser6:latest
'''
                }
                echo 'Goodbye dolly'
            }
        }
    }
}