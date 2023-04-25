pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        
        stage('Compile') {
            steps {
                bat 'mvn -B compile'
            }
        }

        stage('Unit Test') {
            steps {
                bat 'mvn -B test'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn -B package'
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
