pipeline {
    agent any
    tools {
        nodejs 'node'
    }
    environment {
        RENDER_APP_URL = 'https://gallerydevops2.onrender.com'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Allan-Binga/gallery'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'  
            }
        }
        stage('Run tests') {
            steps {
                sh 'npm install mocha'
                sh 'npm test'  
            }
        }
        stage('Deploy to Render') {
            steps {  
                // node server
                echo "App deployed to: ${RENDER_APP_URL}"
            }
        }
    }
    post {
        always {
            slackSend channel: 'allan_ip1',
            message: "Build ID is ${env.BUILD_NUMBER} and app deployed to ${RENDER_APP_URL}"
        }
        failure {
            emailext(
                to: 'allan.binga@student.moringaschool.com',
                subject: "Tests failed.",
                body: "The tests failed because the pipeline could not connect to MongoDB."
            )
        }
    }
}
