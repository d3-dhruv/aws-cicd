pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master', credentialsId: 'git-creds', url: 'https://github.com/d3-dhruv/aws-cicd.git'
            }
        }
        stage('Versioning') {
    steps {
        script {
            sh 'mvn versions:set -DnewVersion=1.0.${BUILD_NUMBER}'
        }
    }
}
        stage('Compile') {
            steps {
                sh 'mvn compile'
                echo 'GITHUB Webhook Configured'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo "testing"
            }
        }
        // stage('File System Scan') {
        //     steps {
        //         sh 'trivy fs --format table --output trivy-fs-report.html .'
        //     }
        // }
    }
}