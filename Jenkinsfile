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

    }
}
