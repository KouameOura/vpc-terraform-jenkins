pipeline {
    agent any

    stages {
        stage('Terraform provision') {
            steps {
                sh """
                    terraform init
                    terraform plan
                    terraform apply --auto-approve
                """
            }
        }
        stage('License to Kill?') {
            steps {
                input message: 'Destroy terraform resources?'
            }
        }
        stage('Search and Destroy') {
            steps {
                sh 'terraform destroy --auto-approve'
                
            }
        }
    }
}