pipeline {
    agent any
    tools {
        nodejs 'node'
    }
    environment {
        RENDER_APP_URL = 'https://gallerydevops.onrender.com/'
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
                sh 'node server.js'  
                echo "App deployed to: ${RENDER_APP_URL}"
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
