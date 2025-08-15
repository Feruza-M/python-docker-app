pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'git@github.com:Feruza-M/python-docker-app.git'
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    sh 'docker build -t python-docker-app .'
                }
            }
        }

        stage('Run Docker container') {
            steps {
                script {
                    // Останавливаем старый контейнер, если он есть
                    sh 'docker rm -f python-docker-app || true'
                    sh 'docker run -d -p 5000:80 --name python-docker-app python-docker-app'
                }
            }
        }
    }
}
