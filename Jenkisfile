pipeline {
    agent {
        docker {
            image 'my-maven-git:latest'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                dir('java-maven/maven') {
                    sh 'mvn clean test package'
                }
            }
        }

        stage('Run Application') {
            steps {
                dir('java-maven/maven') {
                    sh 'java -jar target/*.jar'
                }
            }
        }
    }
}
