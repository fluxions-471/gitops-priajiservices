/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    environment {
        DOCKER_USER = "priajiabror"
        DOCKER_PASS = 'dockerhub-aji2'
    }
    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout from SCM') {
            steps {
                git branch: 'main', credentialsId: 'github-aji', url: 'https://github.com/fluxions-471/gitops-priajiservices.git'
            }
        }
        stage("Push the changed deployment file to Git") {
            steps {
                script {
                    sh """
                        git config --global user.name "Priaji Oktawibyan Abror"
                        git config --global user.email "ajipriaji10@gmail.com"
                        git add .
                        git commit -m "Update Manifest"
                    """

                    withCredentials([gitUsernamePassword(credentialsId: 'github-aji', gitToolName: 'Default')]) {
                        sh "git push https://github.com/fluxions-471/gitops-priajiservices.git main"
                    }
                }
            }
        }
    }
}
