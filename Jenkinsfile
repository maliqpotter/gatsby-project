pipeline {
    agent any
    
    environment {
        // Define the private key as an environment variable
        //CREDS = credentials('server_access') // Make sure to replace 'your-private-key-credential-id' with the ID of your Jenkins credential containing the private key
        SERVER_IP = '62.72.27.60'
        USERNAME = ''
        SSH_PRIVATE_KEY = ''
    }

    stages {

        stage('Get Credentials') {
            steps {
                // Retrieve the username and SSH private key using withCredentials block
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'server_access', keyFileVariable: 'SSH_PRIVATE_KEY', passphraseVariable: '', usernameVariable: 'USERNAME')]) {
                        // Assign the credentials to environment variables
                        USERNAME = env.USERNAME
                        SSH_PRIVATE_KEY = env.SSH_PRIVATE_KEY
                    }
                }
            }
        }

        stage('Checkout') {
            steps {
                // Checkout your source code repository
                git 'https://github.com/maliqpotter/gatsby-project.git'
            }
        }

        stage('Test Connection') {
            steps {
                // Use withCredentials block to securely access your credentials
                script {
                    sh """
                        ssh -o StrictHostKeyChecking=no -i "$SSH_PRIVATE_KEY" $USERNAME@$SERVER_IP 'mkdir test_koneksi'
                    """
                }
            }
        }
        
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
