pipeline {
    agent any

    environment {
        GITHUB_REPO = 'https://github.com/Lyynn777/PhotoBlog.git'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: "${env.GITHUB_REPO}", branch: "${env.BRANCH}"
            }
        }

        stage('Deploy to GitHub Pages') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'github-token', usernameVariable: 'USERNAME', passwordVariable: 'TOKEN')]) {
                    bat '''
                    git config --global user.email "p51061189@gmail.com"
                    git config --global user.name "Jenkins CI"
                    git add docs/
                    git commit -m "Auto update from Jenkins"
                    git push https://%TOKEN%@github.com/Lyynn777/PhotoBlog.git HEAD:main
                    '''

                }
            }
        }
    }
}
