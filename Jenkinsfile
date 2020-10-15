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
            sh 'docker rm $(docker stop $(docker ps -a -q --filter ancestor=dotnetapidemo --format="{{.ID}}"))'
            sh 'docker build -t dotnetapidemo . --no-cache'
            sh 'docker run -t -p 1234:5000 dotnetapidemo -d'
        }
       }
    }
}