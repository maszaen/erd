pipeline {
    agent {
        // Menggunakan image Haskell resmi agar tidak perlu instal manual di Jenkins
        docker { image 'haskell:9.2' }
    }
    stages {
        stage('Checkout') {
            steps {
                // Mengambil kode dari repo fork kamu [cite: 177]
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Updating cabal and installing dependencies...'
                sh 'cabal update'
                sh 'cabal build --only-dependencies'
            }
        }
        stage('Build') {
            steps {
                echo 'Building erd project...' [cite: 123]
                sh 'cabal build'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Running unit tests...' [cite: 129]
                sh 'cabal test'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!' [cite: 216]
        }
        failure {
            echo 'Pipeline failed!' [cite: 219]
        }
    }
}
