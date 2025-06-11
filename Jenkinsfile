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
                    sh '''
                        git config --global user.name "Lyynn"
                        git config --global user.email "you@example.com"
                        
                        git remote set-url origin https://${USERNAME}:${TOKEN}@github.com/Lyynn777/PhotoBlog.git

                        git checkout main
                        git add docs
                        git commit -m "Automated deploy to GitHub Pages from Jenkins" || echo "No changes to commit"
                        git push origin main
                    '''
                }
            }
        }
    }
}
