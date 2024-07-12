pipeline {
    agent any
    tools {
        maven 'maven3' 
        jdk 'java17'
    }
    stages {
        stage('git-code-download') {
            steps {
                echo "Download code from Git"
                git branch: 'main', url: 'https://github.com/devopstechlab/maven-devopsstar.git'
            }
        }
        stage('Build') {
            steps {
                echo "Doing Build"
                sh 'mvn clean package'
            }
        }
        stage('archive-artifacts') {
            steps {
                echo "Archiving the artifacts"
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('build-other-project') {
            steps {
                echo "Build other project which is deploy to dev"
                build wait: false, job: 'deploy-to-dev-pipeline'
            }
        }
    }
}
