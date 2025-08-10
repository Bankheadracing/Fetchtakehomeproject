pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Starting the build process...'

                sh '#!/bin/bash'
                sh 'python3 -m venv venv' // Create a virtual environment
                sh 'pip freeze > requirements.txt'
                sh '. ./venv/bin/activate && pip install -r requirements.txt' // Activate and install
                
                echo 'Build process complete...'
            }
        }
         /*If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.*/
        stage('Test') {
            steps {
                echo 'Running tests on application...'
                sh '#!/bin/bash'
                sh 'python3 -m venv venv'
                sh '. ./venv/bin/activate'
                sh 'sudo apt install python3-pytest-cov python3-coverage'
                //sh 'pip install pytest-cov coverage'
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
