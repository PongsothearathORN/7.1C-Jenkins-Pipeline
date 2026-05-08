// test auto-trigger
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                echo 'Task: Compile the source code and package it into a deployable artifact (e.g., .jar / .war).'
                echo 'Tool: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
                echo 'Task: Run unit tests to verify individual components, then run integration tests to verify components work together correctly.'
                echo 'Tools: JUnit (unit tests), TestNG (integration tests)'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
                echo 'Task: Analyse source code against industry coding standards to detect bugs, code smells, and maintainability issues.'
                echo 'Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
                echo 'Task: Scan source code and third-party dependencies for known vulnerabilities (SAST + SCA).'
                echo 'Tool: OWASP Dependency-Check / Snyk'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
                echo 'Task: Deploy the built artifact to a staging server that mirrors production.'
                echo 'Tool: AWS CLI -> AWS EC2 (staging instance)'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
                echo 'Task: Run integration / end-to-end tests against staging to verify the app works in a production-like environment.'
                echo 'Tools: Selenium / Postman (Newman CLI)'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
                echo 'Task: Promote the validated build from staging to the production server.'
                echo 'Tool: AWS CLI -> AWS EC2 (production instance)'
            }
        }
    }

    post {
        success { echo 'Pipeline executed successfully.' }
        failure { echo 'Pipeline failed.' }
    }
}
