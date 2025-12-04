pipeline {
    agent {
        label 'python'
    }

    stages {
        stage('Entorno') {
            steps {
                sh 'python3 --version'
                sh 'pip3 --version'
                sh 'pip install pytest'
            }
        }

        stage('Descarga') {
            steps {
                git url: 'https://github.com/abeljunior717/pythonOperaciones.git', branch: 'main'
            }
        }

        stage('Ejecutar') {
            steps {
                sh 'python3 operaciones.py'
            }
        }

        stage('Probar') {
            steps {
                sh 'python -m pytest --junitxml=reports/results.xml'
            }
            post {
                always {
                    junit 'reports/results.xml'
                }
            }
        }
    }
}
