pipeline {
    agent any

    stages {
        // stage('Build') { 
        //     steps {
        //         sh 'mvn -B -DskipTests clean package' 
        //     }
        // }

        stage('server'){
          rtSever {
            id: "sf-artifactory"
            url: 'http://52.25.228.74:8081/artifactory'
            username: 'jenkins',
            password: '5Ze0!%rU3d'
            // If you're using Credentials ID:
            //credentialsId: 'ccrreeddeennttiiaall'
            // If Jenkins is configured to use an http proxy, you can bypass the proxy when using this Artifactory server:
            bypassProxy: true
            // Configure the connection timeout (in seconds).
            // The default value (if not configured) is 300 seconds:
            timeout = 300
          }
        }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_TOOL', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                )
            }
        }

        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "sf-artifactory"
                )
            }
        }
    }
}