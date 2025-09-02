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
                sh 'docker run -i --rm --name my-maven-project -v "C:\Users\ACER\Desktop\Work\0000000000\engineer\4-1\240-331\CICD\java-hello-world-with-maven:/usr/src/mymaven" -w /usr/src/mymaven maven:3.9.9 mvn clean install'
            }
        }
        stage('SonarQube') {
            steps {
                sh '''
                docker run -i --rm --name my-maven-project \
                  -v "C:\Users\ACER\Desktop\Work\0000000000\engineer\4-1\240-331\CICD\java-hello-world-with-maven:/usr/src/mymaven" \
                  -w /usr/src/mymaven maven:3.9.9 \
                  mvn clean verify sonar:sonar \
                  -Dsonar.projectKey=test1 \
                  -Dsonar.projectName="test1" \
                  -Dsonar.host.url=http://host.docker.internal:9001 \
                  -Dsonar.token=sqp_fffae0fd28bfa3e761e151cae0a9ef5e33fb2982
                '''
            }
        }
    }
}
