pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/c0losseum/devops_laprak8_5085.git'
                echo 'Repositori berhasil di-clone.'
            }
        }
        stage('Install Dependencies') {
            agent {
                docker { image 'composer:2.5' }
            }
            steps {
                sh 'composer install --no-interaction --no-progress'
                echo 'Instalasi dependensi selesai.'
            }
        }
        stage('Run Unit Test') {
            agent {
                docker { image 'composer:2.5' }
            }
            steps {
                sh 'composer test'
            }
            post {
                success {
                    echo 'Unit test berhasil!'
                }
                failure {
                    echo 'Unit test gagal.'
                }
            }
        }
        stage('Build and Deploy') {
            steps {
                script {           
                    def appImage = docker.build('laprak8-image:latest')
                    sh 'docker stop laprak8-live-app || true'
                    sh 'docker rm laprak8-live-app || true'
                    appImage.run('-d -p 8000:80 --name laprak8-live-app')
                    echo 'Aplikasi berhasil di-deploy dan berjalan di http://localhost:8000'
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline selesai.'
        }
    }
}