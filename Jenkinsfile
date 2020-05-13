pipeline {
    agent any

    stages {
        stage('CleanWorkspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout') {
            steps {
                sh '''
                   git init
                   git config --global user.name "apicurio-ci"
                   git config --global user.email "apicurio-ci@gmail.com"
		               git remote add upstream "https://github.com/riprasad/gitub-actions-demo.git"
                   git remote add origin "https://riprasad:d971f8e848b9f8dd264806d22805524b05acbc58@github.com/riprasad/github-actions-demo-sync-test.git"
		               git pull origin master
                   git fetch upstream
		               ls -al
		               git merge upstream/master --allow-unrelated-histories
		               git push origin master
                   '''
            }
        }
        stage('Sync') {
            steps {
                sh '''
                   git fetch upstream
		               git merge upstream/master --allow-unrelated-histories
		               git push origin master
                   '''
            }
        }
        
    }
}
