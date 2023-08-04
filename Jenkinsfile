pipeline {
    agent { label "build_server" }

    stages {
        stage("This stage will build the package") {
            steps {
                sh "mvn clean"
                sh "mvn install"
                }
            }   
            stage('Copy files to S3') {
            steps {
                script {
                    SOURCE_PATH = "/home/ubuntu/build_server/workspace/build_package/target/WebApp.war"
                    // Use the AWS CLI to copy the file
                    sh "aws s3 cp /home/ubuntu/build_server/workspace/build_package/target/WebApp.war s3://mys301082023"
                    }
                }
            }
        }
}
