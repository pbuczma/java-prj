pipeline{
    agent none
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }
    
    stages {
        stage('build') {
            agent { 
                docker { 
                    image 'maven:3.3.3'
                    // label 'maven-label'
                } 
            }  
            steps {
                sh 'mvn --version'
                echo "Hello ${params.PERSON}"
            }
        }
        stage("after_build"){
            agent { 
                docker { 
                    image 'alpine'
                    label 'maven-label'
                } 
            }
            options {
                timeout(time: 50, unit: 'SECONDS') 
            }
            steps {
                sh 'rm -f file.txt || true'
                sh 'touch file.txt'
                stash includes: 'file.txt', name: 'file' 
                echo "Hello ${params.PERSON}"
            }
        }
        stage("last_stage"){
             agent { 
                 docker { 
                     image 'alpine' 
                     label 'alpine-label'
                 } 
             }
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
