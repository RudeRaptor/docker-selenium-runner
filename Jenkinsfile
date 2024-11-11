pipeline{
    agent any

    stages{
        stage("STARTING GRID IN BACKGROUND MODE"){
            steps{
                bat "docker-compose -f grid.yaml up -d"

            }
        }
        stage("RUNNING TESTS"){
            steps{
                bat "docker-compose -f test-suites.yaml up"
                
            }

        }

    }

    post{

        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
        }
    }   

}


