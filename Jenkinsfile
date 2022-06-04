pipeline {
    agent any
    stages {
        stage('Deploy app on docker swarm from docker-compose file.') {
            steps {
                sh 'docker stack deploy -d docker-compose.yml secretsexample'
            }
        }
        stage('Approval to kill'){
            steps {
                input "Can we stop and remove the stack?"
                sh 'docker stack rm secretsexample'
            }
        }
    }
    post('If fail, stop and remove containers.'){
        failure {
            sh 'docker stack rm secretsexample'
        }
    }
}
