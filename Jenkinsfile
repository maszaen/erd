pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Menarik kode dari repositori GitHub [cite: 177, 179]
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building erd project...' [cite: 123]
                // Karena Jenkins container standar tidak ada Haskell, kita jalankan lewat docker run sementara
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app haskell:9.2 cabal update'
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app haskell:9.2 cabal build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...' [cite: 129]
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app haskell:9.2 cabal test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!' [cite: 216, 231]
        }
        failure {
            echo 'Pipeline failed!' [cite: 219]
        }
    }
}
