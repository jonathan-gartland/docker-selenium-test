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

    }

    post {
            always {
                    // archiveArtifacts artifacts: 'output/**'
                    sh 'docker-compose down'
            }

    }
}
