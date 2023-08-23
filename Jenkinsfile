pipeline {
    agent any
    stages {
        stage (SCM) {
            steps {
                git branch: 'main', url: 'https://github.com/Naveentech1999/pet_shop.git'
            }
        }
        stage('Run Script') {
            steps {
                sh './Scripts/myscript.sh'  
                sh './Scripts/myscript1.sh'
            }
        }
    }
}
