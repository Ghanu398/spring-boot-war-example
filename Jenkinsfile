pipeline {
    agent any 
tools {
    maven 'Maven'
}
    stages{
        stage("testing"){

            steps{
                sh "mvn test"
            }
            
        }
    }
    post {
                always{
                    echo "i will run alway"
                }
                failure{
                    echo "i will only run when pipeline failed"
                }
                success{

                    echo "i will only run when jobs success"
                }

                aborted{

                    echo "i will only run when some one will abort the job"
                }
            }
}
