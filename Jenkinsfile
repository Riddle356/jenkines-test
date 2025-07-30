pipeline {
    agent {
        docker {
            image 'python:3.9-slim'
            args '-v /tmp:/tmp'
        }
    }
    
    stages {
        stage('Setup') {
            steps {
                echo 'Setting up environment...'
                sh 'python --version'
                sh 'pip --version'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Test') {
            steps {
                sh 'pytest -v test_hello.py'
            }
        }
        
        stage('Run') {
            steps {
                sh 'python hello.py'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed - cleaning up'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
