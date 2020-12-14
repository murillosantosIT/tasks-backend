pipeline {
    agent any
    stages {
        stage ('Build Back End') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Testes unitarios') {
            steps {
                bat 'mvn test'
            }
        }
    }
}

