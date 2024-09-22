pipeline {
    agent any 
    tools {
        maven 'Maven'
    }
    parameters {
        booleanParam(name: 'test', defaultValue: true, description: '')
    }
    stages {
        stage("testing") {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    script {
                        if (params.test) {
                            sh "mvn test"
                        } 
                        else {
                            sh "cal" // Replace "cal" with an actual command if needed
                        }
                    }
                    // sh "mvn test"
                }

                
            }
        }

        stage("build") {
            steps {
                sh "mvn package"
            }
        }

        stage("Deploy_to_test") {
            steps {
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }

        stage("Deploy_to_prod") {
            input {
                message "Apply or abort"
                ok "Apply"
            }
            steps {
                deploy adapters: [tomcat7(credentialsId: 'tomcat7details', path: '', url: 'http://54.147.188.18:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
    }

    post {
        always {
            echo "I will run always"
        }
        failure {
            echo "I will only run when the pipeline failed"
        }
        success {
            echo "I will only run when the job succeeds"
        }
        aborted {
            echo "I will only run when someone aborts the job"
        }
    }
}
