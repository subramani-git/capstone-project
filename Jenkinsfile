pipeline {
    agent any
    stages {
        stage('check') {
            when {
                branch 'Dev'
            }
            steps {
                checkout scmGit(branches: [[name: '*/Dev']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-', url: 'https://github.com/subramani-git/capstone-project.git/']])
            }
        }
        stage('SCM') {
            steps {
                git branch: 'Dev', credentialsId: 'git-', url: 'https://github.com/subramani-git/capstone-project.git/'
            }
        }
        stage('docker') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'DOCKER') {
                       sh "docker build -t chrissubramani/dev:latest ." 
                       sh "docker push chrissubramani/dev:latest"
                    }
                }
            }
        }
   
   
    }
}

