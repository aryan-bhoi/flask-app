pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/aryan-bhoi/flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hello-devops .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5001:5000 hello-devops'
            }
        }
    }

    post {
        success {
            echo '✅ Build Successful! Flask app running on http://localhost:5000'
        }
        failure {
            echo '❌ Build Failed. Check console output for details.'
        }
    }
}
