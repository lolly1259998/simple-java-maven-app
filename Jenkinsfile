pipeline {
    agent {
        node {
            label 'build'
        }
    }
    tools {
        maven 'M2_HOME'  // Replace 'M3' with the name of your Maven tool configured in Jenkins
    }
    options {
        timeout(time: 1, unit: 'SECONDS')
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