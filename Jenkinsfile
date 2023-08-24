node {
    try {
        stage('Clone Repository') {
            git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
        }

        // Set execute permissions for the scripts
        sh "chmod +x ./Scripts/myscript.sh"
        sh "chmod +x ./Scripts/myscript1.sh"

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
            if (currentBuild.resultIsBetterOrEqualTo('SUCCESS')) {
                def script2ExitCode = sh(script: './Scripts/myscript1.sh', returnStatus: true)

                if (script2ExitCode == 0) {
                    echo "Script 2 succeeded"
                } else {
                    currentBuild.result = 'FAILURE'
                    error "Script 2 failed"
                }
            }
        }
    } catch (Exception e) {
        currentBuild.result = 'FAILURE'
        error "An error occurred: ${e.getMessage()}"
    } finally {
        echo "Build completed"
    }
    
    if (currentBuild.resultIsBetterOrEqualTo('SUCCESS')) {
        echo "Build is successful"
    } else {
        echo "Build has failed"
    }
}
