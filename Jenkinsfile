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
                sh 'curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py'
                sh 'python3 get-pip.py'
                sh 'pip install pytest'
                sh 'python3 http_e.py'
            }
        }

        stage("Testing ...") {
            steps {
                sh 'pytest TestRest.py'
            }
        }
    }
}
