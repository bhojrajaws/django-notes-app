@Library("Shared") _
pipeline{
    
    agent { label "Pintu"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               script{
                clone("https://github.com/bhojrajaws/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","bhojraj04")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                     docker_push("notes-app","latest","bhojraj04")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
