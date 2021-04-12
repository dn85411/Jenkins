pipeline {

    agent any
	
	

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		powershell '''cd "D:\\cis\\Source\\CORE\\LIVE"
				rebar compile'''
		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\cis\\Source\\Master.sln" /Build "Release" /Project "D:\\cis\\Source\\Install\\AIM PACIS SCU Install\\AIM PACIS SCU Install.vdproj"'
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
