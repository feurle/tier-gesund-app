pipeline {

    options {
        ansiColor('xterm')
    }
    agent any {
        tools {
            jdk 'jdk-21'
            env.JAVA_HOME = "${jdk}"

            gradle 'gradle-8.8'
            env.GRADLE_HOME = "${gradle}"

            echo "jdk installation path is: ${jdk}"

            // next 2 are equivalents
            sh "${jdk}/bin/java -version"

            // note that simple quote strings are not evaluated by Groovy
            // substitution is done by shell script using environment
            sh '$JAVA_HOME/bin/java -version'
        }
    }

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
