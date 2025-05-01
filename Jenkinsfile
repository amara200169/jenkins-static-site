pipeline {
    agent any

    environment {
        DEPLOY_DIR = '/var/www/html'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git(
                    url: 'git@github.com:amara200169/jenkins-static-site.git',
                    branch: 'main',
                    credentialsId: 'github-ssh'
                )
            }
        }

        stage('Deploy to Apache Directory') {
            steps {
                script {
                    // Ensure deployment directory exists and is writable
                    sh """
                    if [ ! -d "$DEPLOY_DIR" ]; then
                        echo "❌ Deployment directory not found: $DEPLOY_DIR"
                        exit 1
                    fi

                    sudo rm -rf $DEPLOY_DIR/*
                    sudo cp -r * $DEPLOY_DIR/
                    echo "✅ Files deployed to $DEPLOY_DIR"
                    """
                }
            }
        }
    }

    post {
        failure {
            echo '🚨 Deployment failed. Please check the logs.'
        }
        success {
            echo '🎉 Deployment completed successfully!'
        }
    }
}
