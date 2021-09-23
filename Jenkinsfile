pipeline {
    agent any
    parameters {
        string(name: 'SOURCE_BRANCH', defaultValue: 'master', description: '...')
        string(name: 'RELEASE_TAG', defaultValue: '', description: '...')
    }
    stages {
        stage('Build and deploy presto zip to artifactory.') {
            steps {

                sh 'echo "Building to version = $RELEASE_TAG"'

                withMaven(maven: 'MAVEN_TOOL') {
                  sh "mvn versions:set -DnewVersion=$RELEASE_TAG"
                  sh "mvn clean install -DskipTests"
                }

                // withCredentials([usernamePassword(credentialsId: 'artifactory-token', usernameVariable: 'AUSR',
                //     passwordVariable: 'APWD')]) {
                //   sh '''curl -X PUT -u $AUSR:$APWD -T presto-server/target/presto-server-$RELEASE_TAG.tar.gz "https://company.com/artifactory/repo/io/presto/$RELEASE_TAG/presto-server-$RELEASE_TAG.tar.gz" '''
                // }
                
                sh 'echo "Done building and tagging to name = $RELEASE_TAG"'
            }
        }
    }
}