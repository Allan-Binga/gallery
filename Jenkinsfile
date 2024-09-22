pipeline {
    agent any
    tools {
        nodejs 'node'
    }
    environment{
        RENDER_APP_URL = 'https://gallerydevops.onrender.com/'
    }
    stages {
        stage ('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Allan-Binga/gallery'
            }
        }
        stage ('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage ('Switch to test branch') {
            steps {
                sh 'git checkout test'
                sh 'npm install'
                echo "App deployed to: ${RENDER_APP_URL}"
            }
        }
        stage ('Run tests') {
            steps {
                sh 'npm test'
            }
        }
        stage ('Deploy to Render') {
            steps {
                sh 'npm install'
                sh 'node server.js'
            }
        }
    }
    post {
        failure {
            emailext(
                to: 'allan.binga@student.moringaschool.com',
                subject: "Tests failed.",
                body: "The tests failed because the pipeline could not connect to MongoDB."
            )
        }
    }
}
