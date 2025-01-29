pipeline {
    agent any

    tools {
        maven '3.9.9'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    dir('exercices/04_exercice') {
                        sh 'mvn compile'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    dir('exercices/04_exercice') {
                        sh 'mvn test'
                    }
                }
            }
        }
        stage('Clean Build') {
            steps {
                script {
                    dir('exercices/04_exercice') {
                        sh 'mvn clean package'
                    }
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'exercices/04_exercice/target/*.jar', allowEmptyArchive: true
            junit 'exercices/04_exercice/target/surefire-reports/*.xml'
        }
    }
}
