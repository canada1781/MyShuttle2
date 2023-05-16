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
        stage('install docker'){
            steps {
                sh "sudo apt update && sudo apt install apt-transport-https ca-certificates curl software-properties-common && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg && 'echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] 'https://download.docker.com/linux/ubuntu' $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null' && sudo apt update && apt-cache policy docker-ce && sudo apt install docker-ce"
                sh "sudo systemctl status docker"    
            }
        }
        stage('build docker image'){
            steps {
                sh "cd /var/jenkins_home/workspace/DemoPipeline/src"
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
