pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C1-80282/practice.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo <token> | /usr/bin/docker login -u heenashinganjude --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t heenashinganjude/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push heenashinganjude/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 heenashinganjude/wywebsite'
            }
        }
    }
}
