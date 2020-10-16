pipeline {
    agent any
    stages {
        stage("Checkout") {
            steps {
                git url: 'https://github.com/falconetpt/dotnet-webapi-docker-example/', branch: 'master'
            }
        }
       stage("run app") {
        steps {
            sh 'kill $(lsof -t -i:1234)'
            sh 'docker rm $(docker stop $(docker ps -a -q --filter ancestor=dotnetapidemo --format="{{.ID}}"))'
            sh 'docker build -t dotnetapidemo . --no-cache'
            sh 'docker run -d -t -p 1234:5000 dotnetapidemo'
        }
       }
    }
}