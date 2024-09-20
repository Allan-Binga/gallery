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
         stage ('Start the server') {
            steps {
                sh 'node server'
            }
        }
       
    }
}