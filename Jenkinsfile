pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script{
                    build()
                }
            }
        }
        stage('Deploy to dev') {
            steps {
                script{
                    deploy("DEV", 1010)
                }
            }
        }
        stage('Test on DEV') {
            steps {
                script{
                    test("DEV")
                }
            }
        }
        stage('Deploy to STG', 1020) {
            steps {
                script{
                    deploy("STG")
                }
            }
        }
        stage('Test on STG') {
            steps {
                script{
                    test("STG")
                }
            }
        }
        stage('Deploy to PROD', 1030) {
            steps {
                script{
                    deploy("PROD")
                }
            }
        }
        stage('Test on PROD') {
            steps {
                script{
                    test("PROD")
                }
            }
        }
    }
}

def deploy(String enviroment, int port){
    echo "Deploying to ${enviroment}"
    bat "pm2 delete ${enviroment}"
    bat "pm2 start -n \"${enviroment}\" index.js --${port}"
}

def test(String enviroment){
    echo "Testing on ${enviroment}"
    bat "npm test"
}

def build(){
    echo "Starting build"
    bat "ls"
    bat "npm install"
}