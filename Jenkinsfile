pipeline {
     agent {
                kubernetes {
                    // defaultContainer 'jnlp'
                    containerTemplate {
                        name 'python'
                        image 'python:3.12-slim'
                        ttyEnabled true
                        command 'cat'
                    }
                }
            }
    
    stages {
        stage('Git checkout') {
            
            steps {
                 cleanWs() 
                git branch: 'main', url: 'https://github.com/fullstackjava082023/Jenkins1HW.git'   
            }
        }

        stage('Run Python Code') {
          
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
