pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'git submodule update --init'
                sh 'hugo --cacheDir "$(pwd)/cache"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'rsync -rv --delete ./public/ /var/www/pipedev/html'
            }
        }
    }
}
