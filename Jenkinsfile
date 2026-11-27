pipeline {
    agent any
    stages {
        stage('build image') {
            steps {
                sh 'docker build -t mon-nginx:latest .'
            }
        }
        stage('run') {
            steps {
                sh 'docker rm -f mon-nginx || true'
                sh 'docker run -d --name mon-nginx -p 8083:80 mon-nginx:latest'
            }
        }
        stage('test') {
            steps {
                sh 'sleep 3'
                sh 'curl localhost:8083'
            }
        }
    }
}
