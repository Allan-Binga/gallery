pipeline {
    agent any
    tools {
        nodejs 'node'
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
            }
        }
        stage ('Run tests') {
            steps {
                sh 'npm test'
            }
        }
    }
    post {
        failure {
            emailext(
                to: 'allan.binga@student.moringaschool.com',
                subject: "Failed running tests.",
                body: "The tests failed because the pipeline could not connect to MongoDB."
            )
        }
    }
}
