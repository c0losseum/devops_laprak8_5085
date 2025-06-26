pipeline {
    agent any

    stages {
        stage('Diagnostik Internal Jenkins') {
            steps {
                echo 'Memulai proses diagnostik dari dalam Jenkins...'

                sh 'echo "======================================================"'
                sh 'echo "--- 1. Memeriksa User dan Grup ---"'
                sh 'echo "Output di bawah ini menunjukkan ID user, grup, dan keanggotaan grup dari proses Jenkins."'
                sh 'id'

                sh 'echo "======================================================"'
                sh 'echo "--- 2. Memeriksa Keberadaan Docker Socket ---"'
                sh 'echo "Mencari file /var/run/docker.sock di dalam container..."'
                sh 'ls -l /var/run/docker.sock'

                sh 'echo "======================================================"'
                sh 'echo "--- 3. Memeriksa PATH Environment Variable ---"'
                sh 'echo "PATH menentukan di direktori mana shell mencari perintah."'
                sh 'env | grep PATH'

                sh 'echo "======================================================"'
                sh 'echo "--- 4. Mencoba Menemukan Perintah docker ---"'
                sh 'which docker || echo "Peringatan: Perintah docker TIDAK DITEMUKAN di PATH"'

                sh 'echo "======================================================"'
                sh 'echo "--- 5. Mencoba Menjalankan Perintah docker Secara Langsung ---"'
                sh 'docker --version'
                
                echo 'Proses diagnostik selesai.'
            }
        }
    }
}
