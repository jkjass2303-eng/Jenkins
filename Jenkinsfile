pipeline {
agent any

stages {

    stage('Display Branch Content') {
        steps {
            script {

                def branch = env.GIT_BRANCH ?: ''

                echo "Current Branch: ${branch}"

                if (branch.contains('main')) {
                    bat '''
                    echo ===== MAIN BRANCH =====
                    type main\\index.txt
                    '''
                }
                else if (branch.contains('dev')) {
                    bat '''
                    echo ===== DEV BRANCH =====
                    type dev\\index.txt
                    '''
                }
                else if (branch.contains('test')) {
                    bat '''
                    echo ===== TEST BRANCH =====
                    type test\\index.txt
                    '''
                }
                else {
                    echo "Branch not configured. Skipping..."
                }
            }
        }
    }
}


}
