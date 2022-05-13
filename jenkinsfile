pipeline {
    agent any
    stages {
        stage('clone') {
            steps {
                git changelog: false, credentialsId: 'github', poll: false, url: 'https://github.com/daravijay1/Studentapp.git'
            }
        }
        stage('clean') {
            steps {
                sh 'mvn clean'
                sh 'java -version'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        /*stage('sonar-code-quality') {
            steps {
			    sh 'mvn sonar:sonar -Dsonar.projectKey=studentapp -Dsonar.host.url=http://34.125.113.13:9000 -Dsonar.login=75d74b43798babfa9d0173b84917465fca2e0922'
            }
        }*/
        stage('Deploy-nexus') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
