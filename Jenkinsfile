node {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
        git "https://github.com/strbaj/Beginning-Jenkins.git"
    }

    dir('Lesson5/ActivityA') {
        stage("Install Requirements") {
            sh 'apk update; apk add make python py-pip'
            sh 'pip install virtualenv'
            sh 'which make'
            sh 'make install'
        }

        stage("Run Tests") {
            sh '/usr/bin/make jenkins_test'
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
