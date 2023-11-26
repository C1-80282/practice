pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_QtzNNSh1noa8I-sJ7ApvMDMltA | /usr/bin/docker login -u heenashinganjude --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t heenashinganjude/myservice .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push heenashinganjude/myservice'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice --replicas 5 -p 9090:80 heenashinganjude/wywebsite'
            }
        }
    }
}
