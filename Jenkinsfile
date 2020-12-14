pipeline {
    agent any
    stages {
        stage ('Build Back End') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Testes unitários') {
            steps {
                bat 'mvn test'
            }
        }
    }
}

