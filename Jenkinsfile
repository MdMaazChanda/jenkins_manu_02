pipeline {
    agent any 
    environment {
        my_account = "${params.MyAccount}"
    }
    parameters {
        choice(name:'MyAccount', choices:['Dev','QA'], description:'Pick AWS Account')
    }
    stages {
        stage('Deploy in Dev') {
            when {
                expression {
                    params.MyAccount == 'Dev'
                }
            }
                steps {
                    sh "echo Building the Projects in Dev AWS Account"
                    getAccountNumber(env.my_account)
                }
        }
        stage('Deploy in QA') {
            when {
                expression {
                    params.MyAccount == 'QA'
                }
            }
                steps {
                    sh "echo Building the Projects in QA AWS Account"
                    getAccountNumber(env.my_account)
                }
        }
        
    }
    post {
        always {
            echo 'Deleting Workspace'
            deleteDir()
        }
    }
}

def getAccountNumber(String AcctName) {
    if (AcctName == 'Dev') {
        sh "echo Hello From Function name, FYI Dev AWS Account ID"
        sh "echo DevID = 8380997850"
    } else (AcctName == 'QA') {
        sh "echo Hello From Function name, FYI QA AWS Account ID"
        sh "echo DevID = 7757037274"
    }
}
