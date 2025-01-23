node { 
 
    stage('Checkout') {
        git branch: "master", url: " https://github.com/shubhamksawant/docker-sonar-jenkins.git"
    }

    stage('Build') {
        sh 'docker build -t my-scanner-new -f Dockerfile.scanner .'
    }

    stage('Scan') {
        docker.image('my-scanner-new').inside('-v /var/run/docker.sock:/var/run/docker.sock --entrypoint=""') {
        sh "/usr/local/bin/sonar-scanner"
        }
    }
}
