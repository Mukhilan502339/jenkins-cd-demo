pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy (Local Cloud)') {
            steps {
                bat '''
                taskkill /F /IM java.exe || exit 0
                start cmd /c "java -jar target\\*.jar"
                '''
            }
        }
    }
}
