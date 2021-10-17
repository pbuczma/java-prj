pipeline{
    options {
        timeout(time: 25, unit: 'SECONDS') 
    }
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("tolong"){
            steps {
                sleep 15
                echo 'Hello'
            }
        }
    }
}
