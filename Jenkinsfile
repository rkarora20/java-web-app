pipeline {
    agent any

    environment {
        TOMCAT_USER = 'tomcat'
        TOMCAT_PASS = 'tomcat'
        TOMCAT_URL = 'http://99.79.194.216:8080'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/rkarora20/java-web-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def warFile = "target/sample-app.war"
                    sh """
                        curl --upload-file ${warFile} \
                        --user ${tomcat}:${tomcat} \
                        ${http://99.79.194.216:8080}/manager/text/deploy?path=/sample-app&update=true
                    """
                }
            }
        }
    }
}
