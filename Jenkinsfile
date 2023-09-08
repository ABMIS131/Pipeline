pipeline {
    agent any

    tools {
        // Define the Maven tool
        maven 'Maven 3.23'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                // Integrate with SonarQube for code analysis 
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                // As an example, using OWASP Dependency-Check
                sh 'dependency-check.sh --project Pipeline --scan ./'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }

    post {
        failure {
            mail body: "The Jenkins job failed. Check attached logs.",
                 subject: "Pipeline failure",
                 to: "abmis131@gmail.com",
                 attachLog: true
        }
    }
}
