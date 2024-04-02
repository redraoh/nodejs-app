pipeline {
    agent any

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/redraoh/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build & deploy') {
            steps {
            // sh 써줘야함
                sh '''
                docker rm -f $(docker ps -qa)
                docker compose down -v
                docker compose up --build -d
                '''
            }
        }
    }
}
