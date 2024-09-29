pipeline {
    agent any
    
    
    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fullstackjava082023/Jenkins1HW.git'   
            }
        }
         stage('Run Python Code') {
            steps {
                sh 'python3 main.py > output.txt'  
            }
        }

         stage('print hello') {
            steps {
               echo 'hello new commit'  
            }
        }
      
        
    }
}
