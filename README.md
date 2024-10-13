A Pipleline code from a Jenkins.


pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[credentialsId: '59415612', url: 'https://github.com/Sujeethrk07/devops_pipeline.git']])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', credentialsId: '59415612', url: 'https://github.com/Sujeethrk07/devops_pipeline.git'
                bat 'python sout.py'   
            }
        }
        stage('Test') {
            steps {
                echo "Testing is done"
            }
        }
    }
}

agent any: This specifies that the pipeline can run on any available Jenkins agent.

Checkout
This stage retrieves the source code from the GitHub repository.
The checkout scmGit command checks out the main branch of the repository specified by the URL.
credentialsId: '59415612': Refers to the stored Jenkins credentials for accessing the repository securely.

Build
This stage pulls the latest code from the 'main' branch again using the git command.
The bat 'python sout.py' command executes the Python script sout.py on a Windows environment using the bat command (if you're running on a non-Windows system, this command should be modified accordingly, such as using sh for Linux).

Test
In this stage, a simple test message is echoed, indicating that testing is complete. Currently, it is a placeholder and can be expanded with actual test steps.
