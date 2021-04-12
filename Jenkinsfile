pipeline {

    agent any
	
	

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		powershell '''cd "D:\\cis\\Source\\CORE\\LIVE"
			rebar compile'''		    
		
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
