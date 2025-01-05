pipeline {
    agent any
    tools {
        sonarQube 'SonarQubeScanner' // Nome configurado no Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Clona o repositório na máquina de build do Jenkins
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner'
                    withSonarQubeEnv('SonarQube') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=juice-shop-lab \
                        -Dsonar.sources=./src \
                        -Dsonar.login=\$SONAR_AUTH_TOKEN
                        """
                    }
                }
            }
        }
    }
}
