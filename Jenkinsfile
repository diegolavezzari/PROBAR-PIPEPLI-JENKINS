pipeline {
    agent any
    environment {
        PATH = "/usr/local/bin:$PATH" // Ajusta esta ruta según la instalación de Docker
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/diegolavezzari/PROBAR-PIPEPLI-JENKINS.git'
            }
        }
        stage('Build and Run') {
            steps {
                script {
                    dir('a') {
                        sh 'docker-compose up -d --build'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'curl -f http://172.17.0.1:5000 || exit 1'
                }
            }
        }
        stage('Clean Up') {
            steps {
                script {
                    dir('a') {
                        sh 'docker-compose down'
                    }
                }
            }
        }
    }
}
