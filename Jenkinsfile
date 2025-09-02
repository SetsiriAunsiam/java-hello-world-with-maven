pipeline {
    agent any

    stages {
        stage('Maven Check') {
            steps {
                sh 'docker run -i --rm --name my-maven-project maven:3.9.9 mvn --version'
            }
        }
        stage('Build') {
            steps {
                sh 'docker run -i --rm --name my-maven-project -v "E:\240-331 Mobile Dev\basic ci-cd\5-Pipeline Jenkins+Sonarqube and Docker\java-hello-world-with-maven:/usr/src/mymaven" -w /usr/src/mymaven maven:3.9.9 mvn clean install'
            }
        }
        stage('SonarQube') {
            steps {
                sh '''
                docker run -i --rm --name my-maven-project \
                  -v "E:\\240-331 Mobile Dev\\basic ci-cd\\5-Pipeline Jenkins+Sonarqube and Docker\\java-hello-world-with-maven:/usr/src/mymaven" \
                  -w /usr/src/mymaven maven:3.9.9 \
                  mvn clean verify sonar:sonar \
                  -Dsonar.projectKey=java-hello-world-with-maven \
                  -Dsonar.projectName='java-hello-world-with-maven' \
                  -Dsonar.host.url=http://172.17.0.2:9000 \
                  -Dsonar.token=sqp_dcfe4c0e61e516e909693dc5df0c7020d83dfeb0
                '''
            }
        }
    }
}
