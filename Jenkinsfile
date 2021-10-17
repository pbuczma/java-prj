pipeline{
    agent { docker { image 'maven:3.3.3' } }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }
    
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sleep 5
                echo "Hello ${params.PERSON}"
            }
        }
        stage("after_build"){
            options {
                timeout(time: 20, unit: 'SECONDS') 
            }
            steps {
                sleep 5
                echo 'Hello'
            }
        }
        stage("last_stage"){
                steps {
                    sleep 5
                    echo 'Hello'
                    sh 'pwd'
                    sh "mkdir ${params.CHOICE}"
                    sh 'ls -1'
                }
            }
        }
}



