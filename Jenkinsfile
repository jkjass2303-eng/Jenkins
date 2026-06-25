pipeline {
    agent any

    stages {

        stage('Branch Information') {
            steps {
                script {

                    BRANCH = env.GIT_BRANCH

                    if (BRANCH == null || BRANCH == '') {
                        BRANCH = sh(
                            script: "git rev-parse --abbrev-ref HEAD",
                            returnStdout: true
                        ).trim()
                    }

                    BRANCH = BRANCH.replace("origin/", "")

                    echo "================================="
                    echo "Current Branch: ${BRANCH}"
                    echo "================================="
                }
            }
        }

        stage('Frontend Build') {
            when {
                expression { BRANCH == 'frontend' }
            }

            steps {
                echo "Frontend branch detected"

                sh '''
                    echo "Running Frontend Build..."
                    pwd
                    ls -la
                '''
            }
        }

        stage('Backend Build') {
            when {
                expression { BRANCH == 'backend' }
            }

            steps {
                echo "Backend branch detected"

                sh '''
                    echo "Running Backend Build..."
                    pwd
                    ls -la
                '''
            }
        }

        stage('Dev Build') {
            when {
                expression { BRANCH == 'dev' }
            }

            steps {
                echo "Dev branch detected"

                sh '''
                    echo "Running Dev Build..."
                    pwd
                    ls -la
                '''
            }
        }
    }

    post {
        success {
            echo "Build completed successfully."
        }

        failure {
            echo "Build failed."
        }
    }
}
