pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                // Clona el repositorio de Git
                git branch: 'main', url: 'https://github.com/diegolavezzari/PROBAR-PIPEPLI-JENKINS.git' // Cambia esto por tu URL
            }
        }
        stage('Build and Run') {
            steps {
                script {
                    // Cambia al directorio donde están tus archivos de Docker
                    dir('a') { // Cambia a la carpeta 'a' donde están Dockerfile y docker-compose.yml
                        // Construir y ejecutar los contenedores
                        sh 'docker-compose up -d --build'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Ejecutar pruebas para verificar que la aplicación está funcionando
                    sh 'curl -f http://localhost:5000 || exit 1' // Asegúrate de que el puerto sea el correcto
                }
            }
        }
        stage('Clean Up') {
            steps {
                script {
                    // Detener y eliminar contenedores
                    dir('a') { // Cambia a la carpeta 'a' para ejecutar docker-compose down
                        sh 'docker-compose down'
                    }
                }
            }
        }
    }
}
