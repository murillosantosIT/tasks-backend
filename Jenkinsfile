pipeline {
    agent any
    stages {
        stage ('Build Back End') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
    }
    stages {
        stage ('Testes unitários') {
            steps {
                bat 'mvn test'
            }
        }
    }
}
