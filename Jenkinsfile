pipeline{
    agent any
    tools {
          maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn test"
            }
            
        }

        stage("Build"){
            steps{
                sh "mvn package"
            }
        }

         stage("Deploy to test"){
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }

        stage("Deploy to prod"){

            input{
                message 'take the code in prod'
                ok 'Apply'
            }
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
