pipeline {

    agent any
	
	

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		bat '''cd "D:\\cis\\Source\\CORE\\LIVE"'''
		bat 'rebar compile'
		bat 'nuget restore D:\cis\Source\Master.sln'
		bat "\"${tool 'MSBuild-Default'}\" D:\cis\Source\Master.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"  
		    
		
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
