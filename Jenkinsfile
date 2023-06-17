pipeline {
    agent any
    stages{
    
        stage('scm') {
            steps {
                // Build the Docker image using the Dockerfile in the repository
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/udhayakr/newdockerfile.git'
            }
        }
        stage('doc build') {
            steps {
                // Build the Docker image using the Dockerfile in the repository
                sh 'docker build -t sant .'
            }
        }
        stage('run') {
            steps {
                // Build the Docker image using the Dockerfile in the repository
                sh 'docker run -itd --name seke -P sant'
            }
        }

        stage('Checkout') {
            steps {
                // Checkout source code from the GitHub repository
                git 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
            }
        }

        stage('Build and Run Docker') {
            steps {
                // Build the Docker image using the Dockerfile in the repository
                sh 'mvn clean install'
            }
        }
    
        stage('Build') {
            steps {
                // Build the Docker image using the Dockerfile in the repository
                deploy adapters: [tomcat9(credentialsId: 'ade06f69-aa16-44df-baa2-43e00c32183b', path: '', url: 'http://13.233.44.205:49153/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
