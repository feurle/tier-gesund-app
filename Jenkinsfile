pipeline {

    agent any
    tools {
        jdk 'jdk-21'
        gradle 'gradle-8.8'
    }
    stages {
        stage('Prepare ...') {
            steps {
                script {
                    def props = readProperties file: 'gradle.properties'
                    env.PROJECT_NAME = props.projectName
                    env.PROJECT_VERSION = props.projectVersion
                    env.DOCKER_URL = props.dockerUrl
                }
            }
        }

        stage('Building ...') {
            steps {
                echo 'Build Java artefact and container image'
                sh 'gradle build bootBuildImage'
            }
        }
        stage('Testing ...') {
            steps {
                echo 'Testing..'
                sh 'gradle test'
            }
        }
        stage('Deploying ...') {
            steps {
                echo 'Push container image to Docker'
                script {
                    withCredentials([usernamePassword(credentialsId: 'DOCKER_USERPASS', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh 'docker login -u $USERNAME -p $PASSWORD'
                        sh 'docker push $DOCKER_URL/$PROJECT_NAME:$PROJECT_VERSION'
                        sh 'docker push $DOCKER_URL/$PROJECT_NAME:latest'
                    }
                }
            }
        }
        stage('Cleanup Image') {
            steps {
                echo 'Remove unused container images'
                script {
                    sh 'docker rmi $DOCKER_URL/$PROJECT_NAME:$PROJECT_VERSION'
                    sh 'docker rmi $DOCKER_URL/$PROJECT_NAME:latest'
                }
            }
        }
    }
}
