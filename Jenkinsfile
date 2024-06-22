pipeline {

    agent any
    tools {
        jdk 'jdk-21'
        gradle 'gradle-8.8'
    }
    environment {

    }
    stages {
        stage('Read Properties') {
            script {
                def props = readProperties file: 'gradle.properties'
                env.PROJECT_NAME = props.projectName
                env.PROJECT_VERSION = props.projectVersion
            }
        }

        stage('Build') {
            steps {
                echo 'Building..'
                sh 'gradle build bootBuildImage'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'gradle test'
            }
        }
        stage('Deploy Image') {
            steps {
                echo 'Deploying....'
                script {
                    withCredentials([usernamePassword(credentialsId: 'DOCKER-USERPASS', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh 'docker login -u $USERNAME -p $PASSWORD'
                        sh 'echo $PROJECT_NAME - $PROJECT_VERSION '

                    }

                }
            }
        }
    }
}
