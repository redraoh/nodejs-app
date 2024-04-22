pipeline {
    agent { label 'agent' }

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/redraoh/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build & deploy') {
            steps {
		sh 'IMAGE_NAME=redraoh/nodejsapp docker compose build'
            }
        }
	stage('docker hub push') {
            steps {
                sh '''
 		   docker login -u redraoh -p dckr_pat_-0m26YU2bcpDJHxnQkbnbT6yP8A
                   docker push siestageek/nodejsapp
		'''
            }
        }
	stage('microk8s run pod') {
            steps {
                sh ' microk8s kubectl run app1 --image=redraoh/nodejsapp '
            }
        }
    }
}
