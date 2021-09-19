pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        // stage('Build') {
        //     steps {
        //         sh 'mvn -B -DskipTests clean package'
        //     }
        // }
        // stage('Test') {
        //     steps {
        //         sh 'mvn test'
        //     }
        //     post {
        //         always {
        //             junit 'target/surefire-reports/*.xml'
        //         }
        //     }
        // }
        // stage('Deliver') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //     }
        // }

        stage('docker build and push to ecr') {
      
            steps {

                    docker ps
                    


            }
        }
    }
}

// node {
//   stage 'Checkout'
//   git 'ssh://git@github.com:irwin-tech/docker-pipeline-demo.git'
 
//   stage 'Docker build'
//   docker.build('demo')
 
//   stage 'Docker push'
//   docker.withRegistry('https://1234567890.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:demo-ecr-credentials') {
//     docker.image('demo').push('latest')
//   }
// }