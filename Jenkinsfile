pipeline{
    options {
        timeout(time: 20, unit: 'SECONDS') 
    }
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sleep 25
                echo 'Build stage'
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
