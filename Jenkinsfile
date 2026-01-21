pipeline {
    agent any

    tools {
        maven 'Maven' // Nombre igual al que puse en Tools, Maven
    }

    stages {
        // Paso 1: Usar GIT desde SCM
        stage('Paso 1: Git Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Paso 2: Compilar') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Paso 3: Test') {
            steps {
                sh 'mvn test'
            }
        }

                stage('Paso 4: Desplegar') {
                    steps {
                        // Generamos el archivo .war
                        sh 'mvn package -DskipTests'
                        sh 'cp target/*.war /var/jenkins_home/tomcat-deploy/'
                    }
                }
    }
}