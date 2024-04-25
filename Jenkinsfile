pipeline {
    agent any
    
    environment {
        // Define the private key as an environment variable
        //CREDS = credentials('server_access') // Make sure to replace 'your-private-key-credential-id' with the ID of your Jenkins credential containing the private key
        SERVER_IP = '62.72.27.60'
    }

    stage{
        stage('Checkout') {
            steps {
                // Checkout your source code repository
                git 'https://github.com/maliqpotter/gatsby-project.git'
            }
        }


        stage('SSH to server') {
          steps {
            sshCommand(
              remote: [
                user: 'root',
                host: '62.72.27.60',
                credentialsId: 'server_access'
              ],
              command: 'mkdir test_connection'
            )
          }
        }
    }
}
