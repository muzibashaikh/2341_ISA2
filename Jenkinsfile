pipeline {
    agent any
    environment {
        PATH = "C:\\Program Files\\Docker\\Docker\\Resources\\bin;${env.PATH}" 
    }
    stages {
        stage('Clone Repository') {
            steps {
                
                bat 'git clone https://github.com/muzibashaikh/2341_ISA2.git'
            }
        }
        
        stage('Build') {
            steps {
                dir('2341_ISA2') {
                    bat 'docker build -t mca2341/2341_MDP -f Dockerfile .'
                }
            }
        }
        stage('Login') {
            steps {
                bat 'docker login -u "mca2341" -p "muzi@dock82" docker.io'
            }
        }
        stage('Push') {
            steps {
                bat 'docker push mca2341/2341_MDP'
            }
        }
        stage('Run in Daemon Mode') {
            steps {
                bat 'docker rm -f 2341'
                // Running the Docker container in daemon mode
                bat 'docker run -d --name 2341 mca2341/2341_MDP'
            }
        }
    }
}
