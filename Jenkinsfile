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
  catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
               
                if (params.test) {
    sh "mvn test"
} else {
    sh "cal"
}

              

  }
                
            }
        }

        stage("build"){
            steps{
                sh "mvn package"
            }
        }

        stage("Deploy_to_test")
        {
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }

         stage("Deploy_to_prod")
        {
            input{
                message "Apply or abort"
                ok "Apply"
                
            }
            steps{
                
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
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
