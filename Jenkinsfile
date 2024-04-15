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
                    deploy("DEV")
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
        stage('Deploy to STG') {
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
        stage('Deploy to PROD') {
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

def deploy(String enviroment){
    echo "Deploying to ${enviroment}"
}

def test(String enviroment){
    echo "Testing on ${enviroment}"
}

def build(){
    echo "Starting build"
}