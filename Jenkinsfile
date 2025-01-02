pipeline {
    agent any
    stages {
        stage('Checkout the code from GitHub') {
            steps {
                git url: 'https://github.com/santu-365/Banking-java-project/'
                echo 'GitHub URL checkout'
            }
        }
        stage('Code compile with Santu') {
            steps {
                echo 'Starting compilation'
                sh 'mvn compile'
            }
        }
        stage('Code testing with Santu') {
            steps {
                sh 'mvn test'
            }
        }
        stage('QA with Santu') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Package with Santu') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Run Dockerfile') {
            steps {
                sh 'docker build -t myimg .'
            }
        }
        stage('Port expose') {
            steps {
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }
    }
}
