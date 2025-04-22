echo 'pipeline {
    agent any

    stages {
        stage("Clone") {
            steps {
                git credentialsId: "github-ssh",
                    url: "git@github.com:amara200169/jenkins-static-site.git"
            }
        }

        stage("Deploy") {
            steps {
                sh "sudo cp -r * /var/www/html/"
            }
        }
    }
}' > Jenkinsfile
