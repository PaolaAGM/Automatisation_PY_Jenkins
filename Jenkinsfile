pipeline {
    agent any
       environment {
            SYSTEM32 = 'C:\\Windows\\System32'
            PYTHON_HOME = 'C:\\Users\\paora\\AppData\\Local\\Programs\\Python\\Python311'
            PYTHON_SCRIPTS = 'C:\\Users\\paora\\AppData\\Local\\Programs\\Python\\Python311\\Scripts'
            PATH = "${SYSTEM32};${PYTHON_HOME};${env.PATH}"
       }

    stages {
        stage('Installer les dépendances') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Exécuter le script') {
            steps {
                bat 'python scraper.py'
            }
        }

        stage('Archiver le fichier CSV') {
            steps {
                archiveArtifacts artifacts: 'data.csv', fingerprint: true
            }
        }
    }
}

