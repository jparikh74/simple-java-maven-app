pipeline {
    agent any

    def server = Artifactory.server "SERVER_ID"

    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}