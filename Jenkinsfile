pipeline {
    agent any
    tools {
        // Specify the Docker installation name as configured in Jenkins
        dockerTool 'docker'
    }
    
    stages {
        stage('Git checkout') {
            
            steps {
                 cleanWs() 
                git branch: 'main', url: 'https://github.com/fullstackjava082023/Jenkins1HW.git'   
            }
        }

        stage('Run Python Code') {
            agent {
                kubernetes {
                    defaultContainer 'jnlp'
                    containerTemplate {
                        name 'python'
                        image 'python:3.12-slim'
                        ttyEnabled true
                        command 'cat'
                    }
                }
            }
            steps {
                sh 'python main.py >> output.txt' 
                // Assuming the file exists in the workspace
                sh 'cat output.txt'                
            }

        }

        stage('Print hello') {
            steps {
               echo 'hello new commit'  
            }
        }
      
        
    }
}
