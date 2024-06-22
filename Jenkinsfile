pipeline {
    options {
        ansiColor('xterm')
    }
    agent any

    stages {
         stage('Info') {
            steps {
                echo "The build number is ${env.BUILD_NUMBER}"
                echo "JAVA_HOME ${env.JAVA_HOME}"
                echo "GRADLE_HOME is ${env.GRADLE_HOME}"
                sh 'java -version'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'gradle clean bootBuildImage'
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
