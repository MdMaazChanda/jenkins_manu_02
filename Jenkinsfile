pipeline {
    agent any 
    environment {
        /*this is custom varible */
        dev_acct = "8380997850"
        qa_acct = "7757037274"
    }
    parameters {
        choice(name:'Account', choices: ['Dev','QA'], description:'Pick AWS Account')
    }
    stages {
        stage('Deploy in Dev') {
            when {
                expression {
                    params.Account == 'Dev'
                }
            }
                steps {
                    sh "echo Building project in Dev Acct ${env.dev_acct}"
                }
        }

        stage ('Deploy in QA') {
            when {
                expression {
                    params.Account == 'QA'
                }
            }
                steps {
                    sh "echo Building project in QA Acct ${env.qa_acct}"
                }
        }
    }
    post {
        always {
            echo 'Deleting Worksapce'
            deleteDir()
        }
    }
}