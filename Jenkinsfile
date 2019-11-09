pipeline{

    agent any

    stages {
	    def mvnHome = tool 'Maven 3.5.0'

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