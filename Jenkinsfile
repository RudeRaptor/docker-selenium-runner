pipeline{
    agent any

    stages{
        stage("RUNNING TESTS"){
            steps{
                bat "docker-compose up"

            }
        }
        stage("BRINGING GRID DOWN"){
            steps{
                bat "docker-compose down"
                
            }

        }
        stage("stage-3"){
            steps{
                echo "Hellooo FUUUUCKS DOCKER EXECUTION"
                
            }

        }
    }   

}


