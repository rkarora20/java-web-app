pipeline {
    agent any

    environment {
        TOMCAT_USER = 'tomcat'
        TOMCAT_PASS = 'tomcat'
        TOMCAT_URL = 'http://localhost:8081'
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
                        --user ${TOMCAT_USER}:${TOMCAT_PASS} \
                        ${TOMCAT_URL}/manager/text/deploy?path=/sample-app&update=true
                    """
                }
            }
        }
    }
}

