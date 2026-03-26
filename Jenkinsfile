pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/your-repo.git'
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
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 5000:5000 --name mycontainer myapp'
            }
        }

        stage('Upload to S3') {
            steps {
                bat 'python upload.py'
            }
        }
    }
}