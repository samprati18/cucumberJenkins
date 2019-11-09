pipeline{

    agent any

    stages {
	    stage 'Checkout'

        // Checkout code from repository
        deleteDir()
        checkout scm

    // Get the maven tool.
    // ** NOTE: This 'M3' maven tool must be configured
    // **       in the global configuration.
    def mvnHome = tool 'M3'


        stage ('Compile Stage') {

            steps {

                sh "${mvnHome}/bin/mvn clean install"

            }
        }
    stage ('Test Stage') {

            steps {

                sh "${mvnHome}/bin/mvn test"

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}