node {
    printMessage("Pipeline Start")

    dir('.') {
        stage("Install Requirements") {
            sh 'apk add make python py-pip'
            sh 'pip install virtualenv'
            sh 'make install'
        }

        stage("Run Tests") {
            sh 'make jenkins_test'
        }

        stage("Deploy") {
            if (env.BRANCH_NAME == "master") {
                printMessage("deploying master branch")
            } else {
                printMessage("no deployment specified for this branch")
            }
        }
    }

    printMessage("Pipeline End")
}

def printMessage(message) {
    echo "${message}"
}
