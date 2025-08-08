pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/amolpatt/CICD.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p /tmp/deploy'
                sh 'cp app.py /tmp/deploy/'
                echo 'Deployment Completed to /tmp/deploy/'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
