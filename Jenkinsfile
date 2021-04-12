pipeline {

  agent {

            label ""
	    def path = ${WORKSPACE}
	    customWorkspace "${path}\\${BUILD_NUMBER}"		

    }
	
	
    //agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..' 
		echo "${WORKSPACE}"
		powershell '''cd "D:\\cis\\Source\\CORE\\LIVE"
				rebar compile'''
		 

		//bat "\"${tool 'MSBuild-Default'}\\MSBuild.exe\" D:\\cis\\Source\\Master.sln /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
		//bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\cis\\Source\\Master.sln" /Build "Release|x64"'
		
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
