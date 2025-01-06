pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Referencia o SonarQube Scanner configurado no Jenkins
                    def scannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    
                    // Configura o ambiente do SonarQube
                    withSonarQubeEnv('SonarQube') { // Nome configurado na seção SonarQube Servers
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=juice-shop-lab \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://192.168.244.139:9000
                        """
                    }
                }
            }
        }
    }
}
