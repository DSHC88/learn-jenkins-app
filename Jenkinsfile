pipeline {
    agent any

    stages {
        stage('Test') {

            steps {
                sh '''
                    #test -f build/index.html
                    npm test
                '''
            }
        }
    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
