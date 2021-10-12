pipeline {
    agent any

    stages {
        stage("run test") {
            steps {
                sh 'docker system prune -f'
                sh 'docker-compose up'
            }
        }
        stage("bring grid down") {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}
