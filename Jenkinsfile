 node {
    stage('Clone Repository') {
        git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
    }

    stage('Run Script 1') {
        def script1ExitCode = sh(script: './Scripts/myscript.sh', returnStatus: true)

        if (script1ExitCode == 0) {
            echo "Script 1 succeeded"
        } else {
            currentBuild.result = 'FAILURE'
            error "Script 1 failed"
        }
    }

    stage('Run Script 2') {
        def previousResult = currentBuild.result
        if (previousResult.isBetterOrEqualTo(hudson.model.Result.SUCCESS)) {
            def script2ExitCode = sh(script: './Scripts/myscript1.sh', returnStatus: true)

            if (script2ExitCode == 0) {
                echo "Script 2 succeeded"
            } else {
                currentBuild.result = hudson.model.Result.FAILURE
                error "Script 2 failed"
            }
        }
    }

    post {
        always {
            echo "Build completed"
        }
        success {
            echo "Build is successful"
        }
        failure {
            echo "Build is failed"
        }
    }
}
