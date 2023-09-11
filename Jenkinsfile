pipeline{
    agent any

    environment{
        DIRECTORY_PATH = 'C:/Users/Natas/OneDrive/Desktop/T14s Sharefolder/0Deakin/SIT223 Professional practice/OnTrack/5.1P'
        TESTING_ENVIRONMENT = 'testing'
        PRODUCTION_ENVIRONMENT = 'Natasha Jiang'
    }

    stages{
        stage('Build'){
            steps{
                echo "Fetch the source code from the directory path specified by the environment variable"
                echo "Compile the code and generate any necessary artifacts"
            }
        }

        stage('Test'){
            steps{
                echo"unit tests"
                echo"integration tests"
            }
        }

        stage('Code Quality Check'){
            steps{
                echo "check the quality of the code"
            }
        }

        stage('Deploy'){
            steps {
                echo "deploy the application to a testing environment specified by the environment variable"
            }
        }

        stage('Approval'){
            steps{
                sleep 10
            }
        }

        stage('Deploy to Production'){
            steps{
                    echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"
                }

            
        }

    }
}