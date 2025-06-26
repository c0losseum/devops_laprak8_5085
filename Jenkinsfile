pipeline {
    agent any
    stages {
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
        }
        stage('Build and Deploy') {
        }
    }
    post {
        always {
            echo 'Pipeline selesai.'
        }
    }
}
