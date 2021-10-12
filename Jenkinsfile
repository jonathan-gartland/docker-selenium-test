pipeline {
    agent any

    stages {

        stage ("start grid") {
            steps {
                sh 'docker system prune -f'
                sh 'docker-compose up --no-color -d selenium-hub chrome firefox'
            }

        }
        stage("run test") {
            steps {
                sh 'docker-compose up search-module'
            }
        }

        stage("bring grid down") {
            steps {
                sh 'docker-compose down'
            }
        }
    }

    post {
            always {
                    archiveArtifacts artifacts: 'output/**'
            }
    }
}
