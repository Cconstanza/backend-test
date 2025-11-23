pipeline {
    agent any
    stages{
        stage("Procesando aplicacion NodeJS"){
            agent { 
                docker {
                    image "node:22"
                }
            }
            stages{
                stage('inicio pipeline'){
                    steps {
                        sh 'echo "iniciando pipeline"'
                    }
                }
                stage('dependencias'){
                    steps {
                        sh 'echo "Instalando dependencias"'
                        sh 'npm install'
                    }
                }
                stage('Lint de codigo'){
                    steps {
                        sh 'echo "Haciendo linter al codigo"'
                        sh 'npm run lint'
                    }
                }
                stage('Ejecutando test y coverage'){
                    steps {
                        sh 'echo "Haciendo testing al codigo"'
                        sh 'npm run test:cov'
                    }
                }
                stage('Ejecutando build'){
                    steps {
                        sh 'echo "Haciendo build del codigo"'
                        sh 'npm run build'
                    }
                }
            }
        }

        stage('Build docker image'){
            steps {
                sh 'docker build -t backend-test .'
                sh 'docker tag backend-test sotoconstanza/backend-test'
                sh "docker tag backend-test sotoconstanza/backend-test:${env.BUILD_NUMBER}"
                script {
                    docker.withRegistry("https://index.docker.io/v1/","id_credenciales_dockerhub") {
                        sh 'docker push sotoconstanza/backend-test'
                        sh "docker push sotoconstanza/backend-test:${env.BUILD_NUMBER}"
                        sh 'docker push sotoconstanza/backend-test'
                        sh "docker push sotoconstanza/backend-test:${env.BUILD_NUMBER}"
                    }
                    docker.withRegistry("https://ghcr.io","credencial-github"){
                        sh 'docker tag backend-test ghcr.io/Cconstanza/backend-test'
                        sh "docker tag backend-test ghcr.io/Cconstanza/backend-test:${env.BUILD_NUMBER}"
                        sh 'docker push ghcr.io/Cconstanza/backend-test'
                        sh "docker push ghcr.io/Cconstanza/backend-test:${env.BUILD_NUMBER}"
                    }
                }
            }
        }
        stage('fin pipeline'){
            steps {
                echo 'finalizando pipeline'
            }
        }
    }
}