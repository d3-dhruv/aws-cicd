pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master' , credentialsId: 'git-cred' , url: 'https://github.com/d3-dhruv/aws-cicd.git'

            }
        }

        stage('Maven Compile') {
            steps {
                echo 'Maven COmpile Started'
                sh 'mvn compile'
                echo 'Maven COmpile Finished'
            }
        }
        stage('Maven Test') {
            steps {
                echo 'Maven Test Started'
                sh 'mvn test'
                echo 'Maven Test Finished'
            }
        }
        stage('File System Scan') {
            steps {
                echo 'Trivy Scan Started'
                sh 'trivy fs --format table --output trivy-fs-output.html .'
                echo 'Trivy Scan Finished'
            }
        }
    }
}