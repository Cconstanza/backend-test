pipeline {
    agent { 
            docker { 
                image "node:22"
                }

    }
    options {
        timeout(time: 1, unit: 'MINUTES')
    }
    stages {
        stage('Inicio pipeline') {
            steps {
                sh 'echo "saludos desde jenkins en terminal"'
            }
        }
        stage('mitad pipeline') {
            steps {
                sh 'echo "saludos desde jenkins la mitad pipeline"'
            }
        }
        stage('dependencias') {
            steps {
                sh 'echo "instalando dependencias"'
                sh 'npm install'
            }
        }
        stage('fin pipeline') {
            steps {
                echo 'saludos desde jenkins en el pipeline'
            }
        }
    }
}
