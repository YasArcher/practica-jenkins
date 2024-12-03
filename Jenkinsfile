pipeline{
    agent any
    environment{
        CONTENEDOR = 'jenkins-Practica'
        IMAGEN = 'jenkins/jenkins:lts'
    }
    stages{
        stage('Preparar Entorno Docker'){
            steps{
                sh "docker stop ${env.CONTENEDOR} || true"
                sh "docker rm ${env.CONTENEDOR} || true"
            }
        }
        stage('Clonar Repositorio'){
            steps{
                script{
                    git 'https://github.com/YasArcher/practica-jenkins.git'
                }
            }
        }
        stage('Construir Imagen'){
            steps{
                script{
                    sh "docker build -t ${env.IMAGEN} ."
                }
            }
        }
        stage('Desplegar Docker'){
            steps{
                script{
                    sh "docker run -d -p 8103:80 --name ${env.CONTENEDOR} ${env.IMAGEN}"
                }
            }
        }
    }
}
