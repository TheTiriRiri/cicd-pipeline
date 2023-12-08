pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/TheTiriRiri/cicd-pipeline.git'
            }
        }
        stage('Build') {
            steps {
                sh './scripts/build.sh'
            }
        }
        stage('Test') {
            steps {
                sh './scripts/test.sh'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t build_konrad_image .'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
