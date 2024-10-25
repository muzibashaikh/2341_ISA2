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
       
        stage('Delete') {
            steps {
                bat 'docker rm -f 2341'
            }
        }
        stage('Run in Daemon Mode') {
            steps {
                // Running the Docker container in daemon mode
                bat 'docker run -d --name 2341 mca2341/2341_MDP'
            }
        }
    }
}
