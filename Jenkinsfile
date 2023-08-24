pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository
                git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
            }
        }

        stage('Set Script Permissions') {
            steps {
                // Set execute permissions for the scripts
               // sh "chmod +x ./Scripts/myscript.sh"
              //  sh "chmod +x ./Scripts/myscript1.sh"
            }
        }

        stage('Run Script 1') {
            steps {
                script {
                    def script1ExitCode = sh(script: './Scripts/myscript.sh', returnStatus: true)
                    
                    if (script1ExitCode == 0) {
                        echo "Script 1 succeeded"
                    } else {
                        currentBuild.result = 'FAILURE'
                        error "Script 1 failed"
                    }
                }
            }
        }

        stage('Run Script 2') {
            when {
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                script {
                    def script2ExitCode = sh(script: './Scripts/myscript1.sh', returnStatus: true)
                    
                    if (script2ExitCode == 0) {
                        echo "Script 2 succeeded"
                    } else {
                        currentBuild.result = 'FAILURE'
                        error "Script 2 failed"
                    }
                }
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
