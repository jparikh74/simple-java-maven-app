pipeline {
    agent any

    def server = Artifactory.server "sf-artifactory"

    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}