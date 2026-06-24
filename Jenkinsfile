pipeline {
    agent any

    parameters {
        choice(
            name: 'BRANCH',
            choices: ['main', 'dev'],
            description: 'Select branch'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: params.BRANCH,
                    url: 'https://github.com/jkjass2303-eng/Jenkins.git'
            }
        }

        stage('Display Content') {
            steps {
                script {
                    if (params.BRANCH == 'main') {
                        bat '''
                        echo ===== MAIN BRANCH =====
                        type main\\index.txt
                        '''
                    }

                    if (params.BRANCH == 'dev') {
                        bat '''
                        echo ===== DEV BRANCH =====
                        type dev\\index.txt
                        '''
                    }
                }
            }
        }
    }
}
