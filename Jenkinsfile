pipeline {
    agent any 
tools {
    maven 'Maven'
}
 parameters{
                        booleanParam(name: 'test', defaultValue: true, description: '')
                }
    stages{
        stage("testing"){
 
 
            steps{

               
                if (params.test == true ) {
                    sh "mvn test"
                } else {
                   sh " echo 'job does not execute and failling'"
                   sh cal

                }

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
