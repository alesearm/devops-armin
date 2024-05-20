pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/winzhaw/DevOpsDocker.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
                // Add your testing steps here
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo deploy'
                // Add your deployment steps here
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub-credentials') {
                        def customImage = docker.build("winzhaw/devopsdocker")
                        customImage.push('latest')
                    }
                }
            }
        }
    }
}
