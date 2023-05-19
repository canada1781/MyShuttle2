pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
              checkout([$class: 'GitSCM', branches: [[name: "master"]],
              userRemoteConfigs: [[credentialsId: 'gitCred', url: "https://github.com/canada1781/MyShuttle2.git"]]])
            }
        }
        stage('find'){
            steps {
                sh "pwd"
                sh "ls -la"
            }
        }
        stage('build docker image'){
            steps {
                sh "cd /var/lib/jenkins/workspace/Demopipeline2/src"
                sh "docker build -t first-image ."
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
