pipeline {
    agent { label 'dagent' }
    options {
        timeout(time: 1, unit: 'MINUTES')
    }
    stages {
        stage('Inicio pipeline') {
            steps {
                sh 'echo "saludos desde jenkins en terminal"'
            }
        }
        stage('fin pipeline') {
            steps {
                echo 'saludos desde jenkins en el pipeline'
            }
        }
    }
}
