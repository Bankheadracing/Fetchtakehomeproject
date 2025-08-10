pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting the build process...'

                sh '#!/bin/bash'
                sh 'python3 -m venv venv' // Create a virtual environment
                sh 'ls -F bin/' 
                sh 'find . -name activate' 
                //sh '. .venv/bin/activate' // Activate and install
                sh 'pip install'
                
                echo 'Build process complete...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests on application...'
                sh '#!/bin/bash'
                sh 'python3 -m venv venv'
                sh '.venv/bin/activate'
                sh 'pip install pytest-cov coverage'
                sh 'pytest --cov=./ --cov-report=xml' // Generate XML report
            // Publish coverage reports using Cobertura Plugin
                cobertura 'coverage.xml'
                echo 'Tests completed on application...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh 'python python Fetch_main.py test2.yaml'
                echo 'Deployed the application to Terminal...'
            }
        }
    }
}
