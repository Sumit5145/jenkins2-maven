pipeline {
    agent any
    tools {
        maven "maven3.9" 
        jdk "java17"
    }
    stages {
        stage('Git Code Downlods') {
            steps {
                git branch: 'main', url: 'https://github.com/Sumit5145/jenkins2-maven.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Arichive the Artifacts') {
            steps {
               archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage(Deploy) {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'jenkins-dev', path: '', url: 'http://34.86.20.224:8090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
