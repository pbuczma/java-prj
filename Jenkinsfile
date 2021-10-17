pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        timeout(unit: 'SECONDS', time: 5) {
            stage("timeout"){
                node {
                    sleep 10
                    echo 'Hello'
                }
            }
        }
    }
}
