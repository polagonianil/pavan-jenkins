pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Specify the branch explicitly
                git url: 'https://github.com/polagonianil/pavan-jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building the project version:1.0... for checking poll scm"
                    // Add your build commands here
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests for version:1.0..."
                    // Add your test commands here
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Adding input step with additional parameters
                    def userInput = input(
                        message: 'Deployment Approval',
                        parameters: [
                            string(name: 'VERSION', defaultValue: '1.0', description: 'Enter the version to deploy'),
                            choice(name: 'ENVIRONMENT', choices: ['dev', 'qa', 'prod'], description: 'Select the environment')
                        ],
                        ok: 'Proceed with Deployment'
                    )
                    echo "Deploying version ${userInput.VERSION} to the ${userInput.ENVIRONMENT} environment..."
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
