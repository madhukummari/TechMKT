pipeline {
    agent any
    
    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages{
        stage("checkout code") {
            steps {
                git url: "https://github.com/madhukummari/TechMKT.git" //, branch: "master"
            }
        }
        stage("test phase") {
            steps {
                sh 'tidy -errors *.html || true'
            }
        }
        stage("deploy to Nginx") {
            steps {
                sshagent(['jenkins-ssh-key']){

                    sh """
                    scp  -r * ubuntu@44.203.148.147:/var/www/html
                    ssh ubuntu@44.203.148.147 'sudo systemctl restart nginx'
                    
                    """
                }

                
            }
        }

    }


}