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
                script{
                    if(fileExists("output/flight/testng-failed.xml") || fileExists("output/vendor-portal/testng-failed.xml"))
                    error("failed tests found !!!")
                }
                
            }

        }

    }

    post{

        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: "output/flight/emailable-report.html", followSymlinks: false
            archiveArtifacts artifacts: "output/vendor-portal/emailable-report.html", followSymlinks: false
        }
    }   

}


