pipeline {
    agent any
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
                    // Reemplaza 'your_username' y 'your_api_token' con tus credenciales
                    sh 'curl -v -u dlavezzari:11a767269b3ba666f989d173dc6024e71f http://172.17.0.1:8080 || exit 1'
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
