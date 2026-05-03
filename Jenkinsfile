pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building erd project...'
                // Kita pakai cabal karena ini proyek Haskell
                sh 'cabal update'
                sh 'cabal build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'cabal test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
