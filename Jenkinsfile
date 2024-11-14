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
    stages {
        stage('Checkout') {
            steps {
                // Ensure the code is checked out to the workspace
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/DSHC88/learn-jenkins-app.git']]
                ])
            }
        }
        stage('Install Dependencies') {
            steps {
                // Confirm the presence of pom.xml before proceeding
                sh 'ls -l $WORKSPACE'
                // Run Maven install
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
