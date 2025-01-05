pipeline {
    agent any
    tools {
        // O tipo correto é "hudson.plugins.sonar.SonarRunnerInstallation"
        hudson.plugins.sonar.SonarRunnerInstallation 'SonarQubeScanner'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner' // Nome configurado no Jenkins
                    withSonarQubeEnv('SonarQube') { // Nome do servidor configurado no Jenkins
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
