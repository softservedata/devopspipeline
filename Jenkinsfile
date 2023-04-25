pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello_World'
            }
        }
        
        stage('Compile') {
            steps {
                sh 'mvn -B compile'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'mvn -B test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B package'
            }
        }

        stage('Integration Test') {
            parallel {
                stage('Running') {
                    agent any
                    steps {
                        bat 'java -jar ./target/lv722contact.war'
                    }
                }
                stage('Integration Test') {
                    steps {
                        sleep 20 // seconds
                       bat 'mvn verify -DskipUnitTests'
                    }
                }
            }
        }
    }
}
