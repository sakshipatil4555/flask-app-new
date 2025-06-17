pipeline {
    agent { label 'vinod' }

    environment {
        APP_NAME = "my-app"      // You can name it whatever you like
    }

    stages {
        stage('code clonning') {
            steps {
                echo 'This is code clonning stage'
                git url: "https://github.com/sakshipatil4555/flask-app-new.git", branch: "main"
                echo 'code clonning successful'
            }
        }

        stage('code building') {
            steps {
                echo 'This is code building stage'
                sh "docker build -t demo-img ."
                echo 'code building successful'
            }
        }

        stage('code running') {
            steps {
                echo 'This is code running stage'
                sh "docker rm -f ${APP_NAME} || true"
                sh "docker run -d -p 80:8000 --name ${APP_NAME} demo-img"
                echo 'Code running successful'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully.'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
