pipeline {

    agent any
    tools {
        gradle 'gradle-8.8'
    }
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
                sh 'gradle build'
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
