pipeline {
    agent any

    stages {
        stage('Build y Unit Test') {
            steps {
                script {
                    sh 'whoami; ls -ltr'
                    sh 'chmod +x gradlew'
                    sh './gradlew clean build'
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
                    sh 'nohup bash gradlew bootRun &'
                    println "Stage: ${env.STAGE_NAME}"
                    sleep 20
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    println "Stage: ${env.STAGE_NAME}"
                    sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'"
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