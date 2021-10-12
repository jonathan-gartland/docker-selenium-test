pipeline {
    agent any

    stages {
        stage("run test") {
            steps {
                sh 'docker system prune -f'
                sh 'docker-compose up --no-color -d selenium-hub chrome firefox'
            }
        }
        stage("bring grid down") {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}
