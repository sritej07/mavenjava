pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Checkout from GitHub') {
            steps {
                deleteDir()
                git url: 'https://github.com/<your-repo>.git', branch: 'main'
            }
        }

        stage('Clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Install') {
            steps {
                bat 'mvn install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Final Output') {
            steps {
                echo "Build Completed Successfully"
            }
        }
    }
}
