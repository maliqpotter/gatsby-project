pipeline {
    agent any
    
    environment {
        // Define the private key as an environment variable
        HOSTNAME = credentials('4b89012a-08fc-4201-9e74-38f48a567284') // Make sure to replace 'your-private-key-credential-id' with the ID of your Jenkins credential containing the private key
        SERVER_IP = '62.72.27.60'
    }

    stages {

        stage('Test Connection') {
            steps {
                script {
                    def hostnameFile = writeFile file: 'temp_hostname', text: HOSTNAME

                    sh "chmod 600 ${hostnameFile}"

                    sh """
                        ssh -o StrictHostKeyChecking=no -i ${hostnameFile} $HOSTNAME:${SERVER_IP} 'mkdir connection_test'
                    """
                }
            }
        }

        //stage('Checkout') {
        //    steps {
        //        // Checkout your source code repository
        //        git 'https://github.com/your/repository.git'
        //    }
        //}
        
        //stage('Build') {
        //    steps {
        //        // Build your application (replace with your build commands)
        //        sh 'mvn clean package'
        //    }
        //}
//
        //stage('Deploy') {
        //    steps {
        //        script {
        //            // Write the hostname credential to a temporary file
        //            def hostnameFile = writeFile file: 'temp_hostname', text: HOSTNAME
//
        //            // Set proper permissions to the hostname file
        //            sh "chmod 600 ${hostnameFile}"
//
        //            // SCP your application artifact to the server
        //            sh """
        //                scp -o StrictHostKeyChecking=no -i ${hostnameFile} target/your-application.jar $HOSTNAME:${SERVER_IP}:/path/to/deployment/directory
        //                # Replace 'your-application.jar' with the name of your application artifact
        //                # Replace '/path/to/deployment/directory' with the directory on the server where you want to deploy your application
        //            """
//
        //            // SSH into the server and execute any additional deployment commands
        //            sh """
        //                ssh -o StrictHostKeyChecking=no -i ${hostnameFile} $HOSTNAME:${SERVER_IP} 'cd /path/to/deployment/directory && ./deploy.sh'
        //                # Replace '/path/to/deployment/directory' with the directory on the server where your application is deployed
        //                # Replace './deploy.sh' with the script or command to execute for deployment
        //            """
        //        }
        //    }
        //}
    }
}
