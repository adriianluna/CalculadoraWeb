pipeline {
    agent any

    tools {
    // Nombre igual al que puse en Tools, Maven
        maven 'Maven'
    }

    stages {
        stage('Github desde SCM') {
            steps {
                checkout scm
            }
        }

        stage('Compilacion') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

                stage('Generamos el war') {

                    steps {

                        sh 'mvn package -DskipTests'
                        sh 'cp target/*.war /var/jenkins_home/tomcat-deploy/'
                    }
                }
    }
}