pipeline{

    agent any

    stages {
	    

        stage ('Compile Stage') {

            steps {
			    def mvnHome = tool 'Maven 3.5.0'

                sh "${mvnHome}/bin/mvn clean install"

            }
        }
    stage ('Test Stage') {

            steps {
			    def mvnHome = tool 'Maven 3.5.0'

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