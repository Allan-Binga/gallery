pipeline{
    agent any
    tools{
        nodejs 'node'
    }
    stages{
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
            }
        }
        stage ('Run tests') {
            steps{
                sh 'npm test'
            }
        }
    }
}