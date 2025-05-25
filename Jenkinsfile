pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/shaikimranmr/E-commerce-project-springBoot.git'
        BRANCH = 'main2'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                dir('JtProject') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Archive Artifacts') {
            steps {
                dir('jt') {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
        }
        failure {
            echo '❌ Build failed.'
        }
    }
}
