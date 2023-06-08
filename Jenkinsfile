pipeline{
    agent any 
    stages{
        stage("cloning ..."){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devopsPRO27/requests']]])

            }
        }
        stage("building ..."){
            steps{
                sh 'python3 http_e.py'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install pytest'
            }
        }

        stage("testing ..."){
            steps{
                sh 'python3 TestRest.py'
            }
        }
    }
}
