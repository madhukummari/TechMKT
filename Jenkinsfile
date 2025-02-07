pipeline {
    agent any
    
    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages{
        stage("checkout code") {
            steps {
                git branch 'master', url: "https://github.com/madhukummari/TechMKT.git" 
            }
        }
        stage("test phase") {
            steps {
                sh 'tidy -errors *.html || true'
            }
        }
        stage("deploy to Nginx") {
            steps {
                sh """
                    scp -r * ubuntu@52.90.61.191:/var/www/html
                    ssh ubuntu@52.90.61.191 'sudo systemctl restart nginx'
                """
            }
        }
        
    }


}