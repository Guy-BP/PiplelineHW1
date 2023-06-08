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
                sh 'python get-pip.py --user'
                sh 'python -m pip install --user pytest'
                sh 'python http_e.py'
            }
        }

        stage("Testing ...") {
            steps {
                sh 'python -m pytest TestRest.py'
            }
        }
    }
}
