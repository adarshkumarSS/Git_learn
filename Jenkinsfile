pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/adarshkumarSS/Git_learn.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker rm -f mycontainer || exit 0'
                bat 'for /f "tokens=1" %i in (\'docker ps -q --filter "publish=5000"\') do docker stop %i'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 5000:5000 --name mycontainer myapp'
            }
        }
    }
}