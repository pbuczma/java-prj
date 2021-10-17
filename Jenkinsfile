pipeline{
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sleep 25
                echo 'Build stage'
            }
        }
        stage("after_build"){
            options {
                timeout(time: 20, unit: 'SECONDS') 
            }
            steps {
                sleep 15
                echo 'Hello'
            }
        }
        stage("last_stage"){
                steps {
                    sleep 15
                    echo 'Hello'
            pwd
                }
            }
        }
}
