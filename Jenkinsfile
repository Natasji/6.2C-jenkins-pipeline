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
                echo "Build automation using Maven"
            }
        }

        stage('Unit and Integration Test'){
            steps{
                echo"unit tests"
                echo"Using JUnit for unit tests, using JMeter for integration tests"
            }
        }

        stage('Code Analysis'){
            steps{
                echo "check the quality of the code"
                echo "Use SonarQube for code quality inspection"
            }
        }

        stage('Security Scan'){
            steps {
                echo "Security Scan using OWASP Dependency-Check"
            }
        }

        stage('Deploy to Staging'){
            steps {
                echo "Deploy using EC2 Jenkins plugin"
            }
        }

        stage('Integration Tests on Staging'){
            steps{
                echo "Using Selenium to run integration test in staging envireonment"
            }
        }

        stage('Deploy to Production'){
            steps{
                    echo "Using Jenkins EC2 plugin to deploy"
                    echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"

                }

            
        }
        post {
            always {
                emailext (
                    to: 'email@example.com',
                    subject: "Jenkins Build: ${currentBuild.fullDisplayName}",
                    body: """<p>START OF THE EMAIL</p>
                    <p>Job Name: ${env.JOB_NAME}</p>
                    <p>Build Number: ${env.BUILD_NUMBER}</p>
                    <p>URL: ${env.BUILD_URL}</p>
                    <p>END OF THE EMAIL</p>""",
                    mimeType: 'text/html'
        )
    }
}


    }
}