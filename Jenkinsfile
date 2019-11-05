node {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
        git "https://github.com/pcigas/Beginning-Jenkins"
    }

    dir('./') {
        stage("Install Requirements") {
            sh 'make install'
            sh 'apt-get install --reinstall make'
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
