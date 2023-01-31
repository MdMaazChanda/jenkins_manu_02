pipeline {
    agent any
    environment {
        registery_url = "https://hub.docker.com/"
        registery = "maaz0816/dock_build_publish"
        registeryCredentials = '03_dockerCreds'
    }
    stages {
        stage ('ImageBuilding') {
            environment {
                registery_endpoint = "${env.registery_url}" + "${env.registery}"
                tag_commit_id = "${env.registery}" + ":$GIT_COMMIT"
            }
            steps {
                script {
                    def applicn = docker.build(tag_commit_id)
                    docker.withRegistry( registery_endpoint, registeryCredentials) {
                        applicn.push()
                    }
                }
            }
        }
        stage('Remove Unused Images') {
            steps {
                sh "docker rmi $registery:$GIT_COMMIT"
            }
        }
    }
    post {
        always {
            echo "Deleting Workspace"
            deleteDir()
        }
    }
}
