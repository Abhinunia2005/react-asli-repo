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
                echo """
Checking out code from Git...
> git fetch --tags --progress -- 
> git checkout main
"""
                sleep 12
            }
        }

        stage('Checkout Code') {
            steps {
                echo """
> git clone https://github.com/fakeuser/fake-repo.git
Cloning into 'fake-repo'...
remote: Enumerating objects: 42, done.
remote: Counting objects: 100% (42/42), done.
"""
                sleep 15
            }
        }

        stage('Terraform Init') {
            steps {
                echo """
Initializing the backend...
Successfully configured the backend "azurerm"!
Terraform has been successfully initialized!
"""
                sleep 8
            }
        }

        stage('Terraform Import') {
            steps {
                echo """
terraform import azurerm_app_service.example /subscriptions/xxx/resourceGroups/fake-rg/providers/Microsoft.Web/sites/fakeapp123
azurerm_app_service.example: Importing from ID...
azurerm_app_service.example: Import prepared!
azurerm_app_service.example: Reading...
azurerm_app_service.example: Import successful!
"""
                sleep 30
            }
        }

        stage('Terraform Plan & Apply') {
            steps {
                echo """
terraform plan
Plan: 2 to add, 0 to change, 0 to destroy.
terraform apply -auto-approve
Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
"""
                sleep 112
            }
        }

        stage('Install Dependencies & Build React') {
            steps {
                echo """
> npm install
added 120 packages, audited 120 packages in 4s

> npm run build
Compiled successfully in 31s
"""
                sleep 92
            }
        }

        stage('Check Build Folder') {
            steps {
                echo """
Checking for 'build' folder...
✅ Build folder exists
"""
                sleep 58
            }
        }

        stage('Deploy to Azure using az webapp deploy') {
            steps {
                echo """
> az webapp deploy --src-path build.zip --name fakeapp123456
Uploading build.zip...
Deployment completed successfully 🎉
"""
                sleep 120
            }
        }

        stage('Declarative: Post Actions') {
            steps {
                echo """
Cleaning up workspace...
Sending notifications...
"""
                sleep 50
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully'
        }
        always {
            echo 'Cleanup done'
        }
    }
}
