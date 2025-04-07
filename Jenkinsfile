pipeline {
    agent any

    environment {
        AZURE_CREDENTIALS_ID = 'fake-sp'
        RESOURCE_GROUP = 'fake-rg'
        APP_SERVICE_NAME = 'fakeapp123456'
    }

    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                echo 'Checking out source code...'
                sleep 1
            }
        }

        stage('Checkout Code') {
            steps {
                echo 'Fake git checkout'
                sleep 1
            }
        }

        stage('Terraform Init') {
            steps {
                echo 'Terraform initialized'
                sleep 8
            }
        }

        stage('Terraform Import') {
            steps {
                echo 'Resources imported'
                sleep 60 // 1 min 4 sec
            }
        }

        stage('Terraform Plan & Apply') {
            steps {
                echo 'Plan and apply done'
                sleep 64
            }
        }

        stage('Install Dependencies & Build React') {
            steps {
                echo 'npm install & build done'
                sleep 74
            }
        }

        stage('Check Build Folder') {
            steps {
                echo 'Build folder verified'
                sleep 1
            }
        }

        stage('Deploy to Azure using az webapp deploy') {
            steps {
                echo 'Fake deploy using az CLI'
                sleep 24
                error("Simulated failure in deploy stage")
            }
        }

        stage('Declarative: Post Actions') {
            steps {
                echo 'Cleanup and notifications'
                sleep 12
            }
        }
    }

    post {
        success {
            echo '✅ Fake pipeline succeeded'
        }
        failure {
            echo '❌ Fake pipeline failed (as expected)'
        }
        always {
            echo 'Cleaning workspace...'
        }
    }
}
