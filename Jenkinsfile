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
        stage('Install Docker') {
          steps {
            script {
          // Install Docker
          sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
          sh 'sh get-docker.sh'
          
          // Add Jenkins user to Docker group
          sh 'sudo usermod -aG docker jenkins'
        }
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
