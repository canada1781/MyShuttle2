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
                sh "su"
                sh "apt-get update"
                sh "apt-get install apt-transport-https ca-certificates curl software-properties-common"
                sh "curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg"
//                 sh "echo 'deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] 'https://download.docker.com/linux/ubuntu' $(lsb_release -cs) stable' | 'sudo tee '/etc/apt/sources.list.d/docker.list' > '/dev/null''"
                sh "apt-get update"
                sh "apt-cache policy docker-ce"
                sh "apt-get install docker-ce"
                sh "systemctl status docker"
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
