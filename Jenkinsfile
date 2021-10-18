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
                echo "Hello ${params.PERSON}"
            }
        }
        stage("after_build"){
            options {
                timeout(time: 50, unit: 'SECONDS') 
            }
            sh 'rm -f file.txt || touch file.txt'
            stash includes: 'file.txt', name: 'file' 
            
            steps {
                 echo "Hello ${params.PERSON}"
            }
        }
        stage("last_stage"){
             agent { docker { image 'alpine' } }
                steps {
                    sleep 5
                    echo 'Hello'
                    unstash 'file'
                    sh 'pwd'
                    sh "rm -rf ${params.CHOICE} || true"
                    sh "mkdir ${params.CHOICE}"
                    sh 'ls -1'
                }
            }
        }
}
