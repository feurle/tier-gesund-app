pipeline {

    agent any
    tools {
        jdk 'jdk-21'
        gradle 'gradle-8.8'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'gradle build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'gradle test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'gradle bootBuildImage'
            }
        }
    }
}
