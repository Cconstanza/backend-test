pipeline {
    agent any
    options {
        timeout(time: 1, unit: 'MINUTES')
    }
    stages {
        stage('Inicio pipeline') {
            steps {
                sh 'echo "saludos desde jenkins en terminal"'
            }
        }
    }
    stages {
        stage('fin pipeline') {
            steps {
                echo 'saludos desde jenkins en el pipeline'
            }
        }
    }
}