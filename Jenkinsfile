pipeline {
    agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Copy') {
            steps {
                sh 'mv target /home/java-app'
            }
        }
        stage('Deliver') {
            steps {
                build job: 'simple-java-app-deliver', wait : false
            }
        }
    }
}
