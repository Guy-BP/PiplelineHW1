pipeline {
    agent any

    stages {
        stage("Cloning ...") {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devopsPRO27/requests']]])
            }
        }

        stage("Building ...") {
            steps {
                sh 'python3 http_e.py'
                sh 'pip install pytest'
            }
        }

        stage("Testing ...") {
            steps {
                sh 'pytest TestRest.py'
            }
        }
    }
}
