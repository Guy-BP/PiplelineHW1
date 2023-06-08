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
                sh 'curl -O https://bootstrap.pypa.io/get-pip.py'
                sh 'python3 get-pip.py --user'
                sh 'python3 -m pip install --user pytest'
                sh 'python3 http_e.py'
            }
        }

        stage("Testing ...") {
            steps {
                sh 'python3 -m pytest TestRest.py'
            }
        }
    }
}
