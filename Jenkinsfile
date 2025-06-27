pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            agent { docker { image 'composer:2.5' } }
            steps {
                sh 'composer install --no-interaction --no-progress'
            }
        }
        stage('Run Unit Test') {
            agent { docker { image 'composer:2.5' } }
            steps {
                sh 'composer test'
            }
        }
        stage('Build and Deploy') {
            steps {
                script {
                    def appImage = docker.build('laprak8-image:latest')
                    sh 'docker stop laprak8-live-app || true'
                    sh 'docker rm laprak8-live-app || true'
                    appImage.run('-d -p 8000:80 --name laprak8-live-app')
                }
            }
        }
    }
}
