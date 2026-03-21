@Library("shared") _
pipeline {
    agent { label "agent01" }

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }    
        stage('Git Checkout') {
            steps {
                script{
                clone("main", "https://github.com/irfanlab/django-notes-app.git")
                }
            }
        }
        stage('Docker Build') {
            steps {
                script{
                dockerbuild("notes-app","latest","irfanlab")
                }
            }
        }
        stage('Push') {
            steps {
                script{
                    echo 'Pushing the image to DockerHub'
                    dockerpush("notes-app","latest","irfanlab")
                
                }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    dockercompose()
                }
            }
        }
    }
}
