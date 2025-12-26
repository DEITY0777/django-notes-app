@Library("Shared") _ 
pipeline{
    agent {label "Agent-first"}
    
    stages{
        
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/DEITY0777/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("django-app", "latest", "rohitsunka")
                }
            }
        }
        stage("Push Image"){
            steps{
                docker_push("django-app", "latest", "rohitsunka")
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying the code"
                 sh '''
                    docker compose down || true
                    docker compose up -d --build
                    '''
            }
        }
    }
}
