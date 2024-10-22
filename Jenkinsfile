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
                    yaml """
                    apiVersion: v1
                    kind: Pod
                    spec:
                      containers:
                      - name: python
                        image: python:3.12-slim
                        command:
                        - cat
                        tty: true
                      - name: jnlp
                        image: jenkins/inbound-agent:4.10-1
                        args:
                        - ${computer.jnlpmac}
                        - ${computer.name}
                    """
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
