pipeline{
    
    agent { label "dev" }
    stages{
        stage("Code Clone"){
            steps{
                echo "Cloning Start"
                git url: "https://github.com/anurag1352/node-todo-cicd.git", branch: "master"
                echo "Cloning Successfull."
            }
        }
        stage("Code Build"){
            steps{
                echo "Image Building Start....."
                sh "docker build -t node-todo-app ."
                echo "Image Build Successful.."
            }
        }
        stage("File & image Scanning"){
            steps{
                sh "trivy fs . -o result.json"
            }
        }
        stage("Code Testing"){
            steps{
                echo "Code Testing Start...."
                echo "Testing Successful"
            }
        }
        stage("Code Deploy."){
            steps{
                echo "Deployment Start..."
                sh "docker-compose down && docker-compose up -d"
                echo "Deployment Done...."
            }
        }
    }
}
