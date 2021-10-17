pipeline{
    options {
        timeout(time: 20, unit: 'SECONDS') 
    }
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("timeout"){
            steps {
                sleep 25
                echo 'Hello'
            }
        }
    }
}
