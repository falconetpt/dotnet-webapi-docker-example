pipeline {
    agent any
    stages {
        stage("Checkout") {
            steps {
                git url: 'https://github.com/falconetpt/dotnet-webapi-docker-example', branch: 'master'
            }
        }
       stage("run app") {
        steps {
            sh 'docker build -t dotnet .'
            sh 'docker run -t -p 1234:5000 dotnetapidemo'
        }
       }
    }
}