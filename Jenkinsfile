pipeline {
    agent any
    stages {
        stage ('Build Servlet Project') {
            steps {
                /*For windows machine */
               echo 'Maven Now Clean Package ....'
				
               //bat  'mvn clean package'

                /*For Mac & Linux machine */
                sh  'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving ....'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
		stage ('Create Tomcat Docker Image') {
            steps{
                sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"

                //bat "docker build . -t tomcatwebapp:${$env.BUILD_ID}"

            }
        }		
    }
}
