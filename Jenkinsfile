pipeline {
    agent any

    stages {
        stage("run test") {
            steps {
                sh 'docker system prune -f'
                sh 'docker-compose up --no-color -d selenium-hub chrome firefox'
                sh 'docker-compose up search-module'
            }
        }
        stage("bring grid down") {
            steps {
                sh 'docker-compose down'
            }
        }

        post {
            always {
                archiveArtifacts artifacts: 'output/**'
            }
        }
    }
}
