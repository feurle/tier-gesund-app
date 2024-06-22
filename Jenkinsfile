pipeline {
    options {
        ansiColor('xterm')
    }
    agent any

    stages {
         stage('Info') {
            steps {
                echo 'Build number .. ${env.BUILD_NUMBER}'
                echo "The build number is ${env.BUILD_NUMBER}"
                echo "You can also use \${BUILD_NUMBER} -> ${BUILD_NUMBER}"
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
