pipeline {
    agent any

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
                    containerTemplate {
                        name 'python'
                        image 'python:3.12-slim'
                        ttyEnabled true
                        command 'cat'
                    }
                }
            }
            steps {
                container('python') {
                    sh 'python main.py >> output.txt'
                    sh 'cat output.txt'
                }
            }
        }

        stage('Print hello') {
            steps {
                echo 'hello new commit'
            }
        }
    }
}
