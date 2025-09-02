pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Run Maven inside a Docker container without -it
                    sh 'docker run --rm --name my-maven-project maven:3.9.9 mvn --version'
                }
            }
        }
    }
}
