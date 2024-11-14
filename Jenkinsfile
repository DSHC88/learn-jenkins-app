pipeline {    
    agent {
        docker {
            image 'maven:3.9.9-amazoncorretto-23-alpine'
            args '-v /dev/bus/usb:/dev/bus/usb'  // For device access if needed
        }
    }
    environment {
        MAVEN_OPTS = '-Dmaven.repo.local=${WORKSPACE}/.m2/repository' // Define a custom repository path
    }
    stages{
        stage('Install Dependencies') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
        post {
        always {
            cleanWs()
        }
    }

}
