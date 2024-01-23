pipeline {
    agent {
            docker {
                image "maven:3.9.6-amazoncorretto-21-al2023"
                label "docker"
//                 args "-v /tmp/maven:/var/maven/.m2 - e MAVEN_CONFIG=/var/maven/.m2"
            }
    }
    stages {
        stage('Build') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                // sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}

