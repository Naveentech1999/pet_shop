pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository
                 git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
            }
        }
stage('Script') {
            steps {
                echo "Running Script 1..."
                sh './Scripts/myscript.sh'
            }
        }
    }
}
