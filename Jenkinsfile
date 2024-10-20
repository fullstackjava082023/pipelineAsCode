pipeline {
    agent any
    tools {
        // Specify the Docker installation name as configured in Jenkins
        dockerTool 'docker'
    }
    
    stages {
        stage('Git checkout') {
            
            steps {
                git branch: 'main', url: 'https://github.com/fullstackjava082023/Jenkins1HW.git'   
            }
        }
         stage('Run Python Code') {
             agent {
                docker {
                    image 'python:3.12-slim' // Using the official Python Docker image
                    args '-u root'
                }
            }
            steps {
                sh 'python main.py >> output.txt' 
                // Assuming the file exists in the workspace
                sh 'cat output.txt'                
            }

        }

         stage('print hello') {
            steps {
               echo 'hello new commit'  
            }
        }
      
        
    }
}
