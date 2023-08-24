pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository
                 git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
            }
        }
stage('Run Script 1') {
            steps {
                echo "Running Script 1..."
                sh './Scripts/myscript.sh'
            }
        }

        stage('Run Script 2') {
            steps {
                echo "Running Script 2..."
                sh './Scripts/myscript1.sh'
            }
        }
    }
}
