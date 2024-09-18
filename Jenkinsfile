pipeline{
    agent{
        label any
    }
    tools {
          maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn --version"
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
