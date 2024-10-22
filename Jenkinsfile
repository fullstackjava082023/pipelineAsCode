pipeline {
    agent {
        kubernetes {
            label 'python-agent'
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
    image: jenkins/inbound-agent:latest
    args: ['${JENKINS_SECRET}', '${JENKINS_NAME}']
    env:
    - name: JENKINS_URL
      value: "${JENKINS_URL}"
"""
        }
    }

    stages {
        stage('Run Python Code') {
            steps {
                container('python') {
                    sh 'python --version'
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
