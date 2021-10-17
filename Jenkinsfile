timeout(unit: 'SECONDS', time: 5) {

    node { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("timeout"){
            steps {
                sleep 10
                echo 'Hello'
            }
        }
    }
}
