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
        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=sonar -Dmaven.test.skip=true';
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