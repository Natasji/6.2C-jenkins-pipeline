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
                echo"Using JUnit for unit tests, using JMeter for integration tests"
            }
            post{
                success{
                    emailext(
                        to: "njiang55@gmail.com",
                        subject: "Test Stage passed: ${currentBuild.fullDisplayName}",
                        body: "Job Name: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nURL: ${env.BUILD_URL} test was successful",
                        attachLog: true 
                    )               
                }
                failure{
                    emailext(
                        to: "njiang55@gmail.com",
                        subject: "Test Stage failed: ${currentBuild.fullDisplayName}",
                        body: "Job Name: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nURL: ${env.BUILD_URL} test failed",
                        attachLog: true 
                    )
                                                       
                }
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
            post {
                always {
                    script {
                        if (currentBuild.result == 'FAILURE') {
                            emailext (
                                to: 'njiang55@gmail.com',
                                subject: "Security Scan Failed: ${currentBuild.fullDisplayName}",
                                body: "Job Name: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nURL: ${env.BUILD_URL}",
                                attachLog: true,
                                mimeType: 'text/plain'
                            )
                        } else {
                            emailext (
                                to: 'njiang55@gmail.com',
                                subject: "Security Scan Passed: ${currentBuild.fullDisplayName}",
                                body: "Job Name: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nURL: ${env.BUILD_URL}",
                                attachLog: true,
                                mimeType: 'text/plain'
                            )
                        }
                    }
                }
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


    }
}