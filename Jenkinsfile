pipeline {
    agent any

    stages {
        stage('Build y Unit Test') {
            steps {
                script {
                    sh './gradle clean build'
                    println "Stage: ${env.STAGE_NAME}"
                }
            }
        }
        stage('Sonar') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'; 
                    withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.sources=src -Dsonar.java.binaries=build"
                    }                }
            }
        }
        stage('Run') {
            steps {
                script {
                    sh './gradle clean build'
                    println "Stage: ${env.STAGE_NAME}"
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    println "Stage: ${env.STAGE_NAME}"
                }
            }
        }
        stage('Nexus') {
             steps {
                script {
                    println "Stage: ${env.STAGE_NAME}"
                }
            }
        }  
    }
}