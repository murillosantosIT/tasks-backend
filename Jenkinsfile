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
        stage ('Sonar Analysis') {
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                    bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://localhost:9000 -Dsonar.login=f75f7ce80bf4c64932101272eab3f18d951f936f -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java"
                }                
            }
        }
        stage ('Quality Gate') {
            steps {
                sleep(60)
                timeout(time: 1, unit: 'MINUTES') {
                    def qg = waitForQualityGate()
                    print "Finished waiting"
                    if (qg.status != 'OK') {
                        error "Pipeline aborted due to quality gate failure: ${qg.status}"
                    }
                }  
            }
        }
    }
}

