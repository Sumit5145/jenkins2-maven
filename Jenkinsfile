pipeline {
    agent any
    tools {
        maven 'maven3.9'
        jdk 'java17'
    }
    stages {
        stage('Git-Code-Downlods') {
            steps {
                git branch: 'main', url: 'https://github.com/Sumit5145/jenkins2-maven.git'
            }
        }
        stage('Build') {
            steps {
               sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                junit stdioRetention: '', testResults: '**/target/surefire-reports/*xml'
            }
        }
        stage('Archive-Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('new-deploy-dev') {
            steps {
            build wait: false, job: 'new-deploy-dev'   
            }
        }
    }
}
