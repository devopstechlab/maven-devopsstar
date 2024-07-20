pipeline {
    agent any
    stages {
        stage('git-code-download') {
            steps {
                echo "Download code from Git"
                git branch: 'main', url: 'https://github.com/devopstechlab/maven-devopsstar.git'
            }
        }
        stage('create-docker-image') {
            steps {
                sh '''
                docker build -t devopstechlab/tomcatstar:${BUILD_NUMBER}
                docker tag devopstechlab/tomcatstar:${BUILD_NUMBER} devopstechlab/tomcatstar:latest
                docker push devopstechlab/tomcatstar:${BUILD_NUMBER}
                docker push devopstechlab/tomcatstar:latest
                '''
            }
        }
    }
}
