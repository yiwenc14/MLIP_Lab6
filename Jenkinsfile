pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step'
                echo 'In Python, we can build our package here or skip this step'
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo 'Test Step: We run testing tool like pytest here'

                 # Create virtual environment if it doesn't exist
                if [ ! -d "mlip" ]; then
                    python3 -m venv mlip
                fi
	
		# Activate the virtual environment
                source mlip/bin/activate

		# Upgrade pip within the venv
                pip install --upgrade pip

		# Install dependencies inside the virtual environment
                pip install pandas pytest scikit-learn

                # Run pytest
                pytest

		# Deactivate the virtual environment
                deactivate
		
                #echo 'pytest not runned'
                #exit 1 #comment this line after implementing Jenkinsfile
                '''

            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our porject'
                echo 'Depending on the context, we may publish the project artifact or upload pickle files'
            }
        }
    }
}
