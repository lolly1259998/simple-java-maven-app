pipeline {
    agent any  // Run on any available node
    tools {
        maven 'M2_HOME'  // Ensure this matches your Maven tool configuration in Jenkins
    }
    options {
        timeout(time: 30, unit: 'MINUTES')  // Increased timeout
    }
    environment {
        APP_ENV = "DEV"
    }
    stages {
        stage('Code Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
        stage('SonarQube') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.token=squ_75ec5f123179a9c2f52a8d9c5ae0095c0fc883a6 -Dmaven.test.skip=true';
            }
        }
    }
    post {
        always {
            echo "======always======"
        }
        success {
            echo "=====pipeline executed successfully ====="
        }
        failure {
            echo "======pipeline execution failed======"
        }
    }
}