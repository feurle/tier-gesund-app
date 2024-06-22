pipeline {
    options {
        ansiColor('xterm')
    }
    agent any

    stages {
         stage('Info') {
            steps {
                echo "The build number is ${env.BUILD_NUMBER}"
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
