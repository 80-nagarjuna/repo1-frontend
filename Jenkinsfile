pipeline {
    agent any
    stages {
        stage('Checkout Repo1') {
            steps {
                dir('frontend') {
                    git branch: 'feature-login',
                        url: 'https://github.com/80-nagarjuna/repo1-frontend.git'
                }
            }
        }
        stage('Checkout Repo2') {
            steps {
                dir('assets') {
                    git branch: 'feature-login',
                        url: 'https://github.com/80-nagarjuna/repo2-assets.git'
                }
            }
        }
        stage('Build & Archive') {
            steps {
                sh '''
                mkdir -p build
                cp frontend/index.html build/
                cp frontend/style.css build/
                cp assets/version.txt build/
                cp assets/logo.txt build/
                tar -czf website.tar.gz build
                '''
                archiveArtifacts artifacts: 'website.tar.gz'
            }
        }
    }
}
