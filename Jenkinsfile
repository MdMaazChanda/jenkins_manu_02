pipeline {
    agent any 
    stages {
        satge ('User Input Example') {
            input {
                message "HI Press Something to Proceed Further"
                ok "Proceed"
                submitter "maaz,nusaiba"
                parameters {
                    string(name: 'Person', defaultvValue:'MaazNusaiba', description: 'Who Should I say Hello To')
                }
            }
            steps {
                echo "Hello, ${Person}, nice to have you in mey life"
            }
        }
    }