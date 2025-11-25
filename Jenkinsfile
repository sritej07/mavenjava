pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/sritej07/mavenjava.git'
            }
        }

        stage('Build WAR') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(credentialsId: 'tomcat', path: '', 
                        url: 'http://localhost:8080')
                ], war: 'target/mywebapp.war'
            }
        }
    }

    post {
        success {
            echo "Deployment successful!"
        }
    }
}
