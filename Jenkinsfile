pipeline {
    agent any
    tools {
        jdk 'OpenJDK8'
        maven 'Maven3'
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/sarab321/CICDPipeline.git'
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                    sh "docker build -t sarab321/adi_repo:$BUILD_NUMBER ."
                    sh "docker push sarab321/adi_repo:$BUILD_NUMBER"
}
                }
            }
        }
    }
}
