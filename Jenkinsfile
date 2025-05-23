pipeline {
    agent any
    
    stages {
        // Uncomment the below stage if you configured SonarQube
        // stage('Run Sonarqube') {
        //     environment {
        //         scannerHome = tool 'sonarqubescanner'
        //     }
        //     steps {
        //         withSonarQubeEnv(credentialsId: 'sonarqube', installationName: 'sonarqubeserver') {
        //             sh "${scannerHome}/bin/sonar-scanner"
        //         }
        //     }
        // }

        stage('Build Docker images on Build Server') {
            steps {
                script {
                    // Execute Ansible playbook on Build Server
                    sh "ssh msuryaprasad11@10.0.0.5 'ansible-playbook /home/msuryaprasad11/build.yaml'"
                }
            }
        }
        
        stage('Deploy Script on Deploy Server') {
            steps {
                script {
                    // Execute deployment playbook on Deploy Server
                    sh "ssh msuryaprasad11@10.0.1.3 'ansible-playbook /home/msuryaprasad11/deploy.yaml'"
                }
            }
        }
    }
}
